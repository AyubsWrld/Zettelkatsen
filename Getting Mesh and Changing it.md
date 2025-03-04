```c++
// Fill out your copyright notice in the Description page of Project Settings.
#include "MonitorActor.h"
#define SCREEN_MATERIAL_INDEX 2 // Index for screen material 

// Sets default values
AMonitorActor::AMonitorActor()
{
	PrimaryActorTick.bCanEverTick = true;
}



/*
* @signature : GetScreenMaterial() 
* @return    : Returns UMaterialInstance ptr to Display.
* @purpose   : 
*/

 UMaterialInstanceDynamic* AMonitorActor::GetScreenMaterial() {
	UStaticMeshComponent* Mesh = Cast<UStaticMeshComponent>(GetComponentByClass(UStaticMeshComponent::StaticClass()));
	UMaterialInterface* MaterialInterface = Mesh->GetMaterial(2); 
	UMaterialInstanceDynamic* DynamicScreenInstance = Mesh->CreateDynamicMaterialInstance( SCREEN_MATERIAL_INDEX , MaterialInterface); 
	if (!DynamicScreenInstance) {
		UE_LOG(LogTemp, Warning, TEXT("Could not retrieve screen instance")); 
		return nullptr ; 
	}
	return DynamicScreenInstance ;
}

/*
* @signature :
* @return    :
* @param     :
* @purpose   : 
*/

 void AMonitorActor::SetDisplay( UMaterialInstanceDynamic* Display , float iValue ) {
	 Display->SetScalarParameterValue("Intensity", iValue ); 
}


void AMonitorActor::BeginPlay()
{
	UMaterialInstanceDynamic* Screen = AMonitorActor::GetScreenMaterial();
	SetDisplay(Screen, 0.3f) ;
}


void AMonitorActor::Tick(float DeltaTime)
{
	Super::Tick(DeltaTime);
}


```