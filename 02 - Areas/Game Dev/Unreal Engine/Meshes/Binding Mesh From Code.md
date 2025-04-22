```cpp 

// 1. Create a StaticMeshComponent (this is the visual component attached to your actor)
UStaticMeshComponent* Mesh = CreateDefaultSubobject<UStaticMeshComponent>(TEXT("MeshComp"));

// 2. Load the actual UStaticMesh asset
static ConstructorHelpers::FObjectFinder<UStaticMesh> MeshAsset(TEXT("/Game/StarterContent/Shapes/Shape_Cone.Shape_Cone"));

// 3. If it loaded correctly, assign it to the Mesh Component
if (MeshAsset.Succeeded())
{
    Mesh->SetStaticMesh(MeshAsset.Object);
}

```

1) Create an object of type `UStaticMeshComponent`.
2) `ConstructorHelpers::FObjectFinder<T>` is used to load assets of type T from the disk. 
3) If the the value resolved and succeeded we can assign it to the object.

> [!tip] **Retrieving file reference**
> We can retrieve the reference for the files by right clicking them within the content browser and selecting copy reference.

___
Tags: #unreal-engine #cpp #meshes