#### `MonitorActor.cpp`

```c++
#include "MonitorActor.h"

// Sets default values
AMonitorActor::AMonitorActor()
{
 	// Set this actor to call Tick() every frame.  You can turn this off to improve performance if you don't need it.
	PrimaryActorTick.bCanEverTick = true;

}

// Called when the game starts or when spawned
void AMonitorActor::BeginPlay()
{
	Super::BeginPlay();
	
}

// Called every frame
void AMonitorActor::Tick(float DeltaTime)
{
	Super::Tick(DeltaTime);

}


```


#### `MonitorActor.h`

```c++
// Fill out your copyright notice in the Description page of Project Settings.

#pragma once

#include "CoreMinimal.h"
#include "GameFramework/Actor.h"
#include "MonitorActor.generated.h"

UCLASS()
class ANGELA_API AMonitorActor : public AActor
{
	GENERATED_BODY()
	
public:	
	// Sets default values for this actor's properties
	AMonitorActor();

protected:
	// Called when the game starts or when spawned
	virtual void BeginPlay() override;

public:	
	// Called every frame
	virtual void Tick(float DeltaTime) override;

};

```

___
Tags : #programming #game-dev #unreal-engine #cpp