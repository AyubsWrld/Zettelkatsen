```c++
UStaticMeshComponent* MeshComponent = Cast<UStaticMeshComponent>(GetComponentByClass(UStaticMeshComponent::StaticClass()));
if (MeshComponent)
{
    UStaticMesh* Mesh = MeshComponent->GetStaticMesh();
    UE_LOG(LogTemp, Warning, TEXT("Actor %s has Static Mesh: %s"), *GetName(), *Mesh->GetName());
}
```


### Breakdown 
___
   

___
Tags : #programming #game-dev #unreal-engine #cpp