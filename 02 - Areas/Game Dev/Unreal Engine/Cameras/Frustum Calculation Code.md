```cpp
void ASurveillanceCam::DrawFrustum()
{
    UWorld* World = GetWorld();
    if (!World || !surveillance_camera_)
        return;

    // Get camera properties
    FVector CameraLocation = surveillance_camera_->GetComponentLocation();
    FRotator CameraRotation = surveillance_camera_->GetComponentRotation();

    // Use a more pronounced FOV angle if the camera's is too narrow
    float FOVAngle = FMath::Max(surveillance_camera_->FOVAngle, 60.0f);

    // Define a fixed aspect ratio if MONITOR constants aren't working properly
    // Typical 16:9 aspect ratio
    float AspectRatio = 16.0f / 9.0f;


    // Define frustum distances with more separation
    float NearDist = 50.0f;
    float FarDist = 1000.0f;

    // Calculate the frustum dimensions
    float HalfFOVRad = FMath::DegreesToRadians(FOVAngle * 0.5f);
    float NearHeight = 2.0f * FMath::Tan(HalfFOVRad) * NearDist;
    float NearWidth = NearHeight * AspectRatio;
    float FarHeight = 2.0f * FMath::Tan(HalfFOVRad) * FarDist;
    float FarWidth = FarHeight * AspectRatio;

    // Get the camera's axes
    FVector Forward = surveillance_camera_->GetForwardVector();
    FVector Right = surveillance_camera_->GetRightVector();
    FVector Up = surveillance_camera_->GetUpVector();

    // Calculate the 8 corners of the frustum
    FVector NearTopLeft = CameraLocation + Forward * NearDist - Right * (NearWidth * 0.5f) + Up * (NearHeight * 0.5f);
    FVector NearTopRight = CameraLocation + Forward * NearDist + Right * (NearWidth * 0.5f) + Up * (NearHeight * 0.5f);
    FVector NearBottomLeft = CameraLocation + Forward * NearDist - Right * (NearWidth * 0.5f) - Up * (NearHeight * 0.5f);
    FVector NearBottomRight = CameraLocation + Forward * NearDist + Right * (NearWidth * 0.5f) - Up * (NearHeight * 0.5f);

    FVector FarTopLeft = CameraLocation + Forward * FarDist - Right * (FarWidth * 0.5f) + Up * (FarHeight * 0.5f);
    FVector FarTopRight = CameraLocation + Forward * FarDist + Right * (FarWidth * 0.5f) + Up * (FarHeight * 0.5f);
    FVector FarBottomLeft = CameraLocation + Forward * FarDist - Right * (FarWidth * 0.5f) - Up * (FarHeight * 0.5f);
    FVector FarBottomRight = CameraLocation + Forward * FarDist + Right * (FarWidth * 0.5f) - Up * (FarHeight * 0.5f);

    // Draw the frustum using debug lines with better visibility
    bool bPersistentLines = true;
    float Duration = 0.0f; // Only matters if not persistent

    // Use thicker lines and brighter colors
    float Thickness = 3.0f;
    FColor NearColor = FColor::Yellow;
    FColor FarColor = FColor::Green;
    FColor ConnectColor = FColor::Blue;

    // Draw near plane with a distinct color
    DrawDebugLine(World, NearTopLeft, NearTopRight, NearColor, bPersistentLines, Duration, 0, Thickness);
    DrawDebugLine(World, NearTopRight, NearBottomRight, NearColor, bPersistentLines, Duration, 0, Thickness);
    DrawDebugLine(World, NearBottomRight, NearBottomLeft, NearColor, bPersistentLines, Duration, 0, Thickness);
    DrawDebugLine(World, NearBottomLeft, NearTopLeft, NearColor, bPersistentLines, Duration, 0, Thickness);

    // Draw far plane with another color
    DrawDebugLine(World, FarTopLeft, FarTopRight, FarColor, bPersistentLines, Duration, 0, Thickness);
    DrawDebugLine(World, FarTopRight, FarBottomRight, FarColor, bPersistentLines, Duration, 0, Thickness);
    DrawDebugLine(World, FarBottomRight, FarBottomLeft, FarColor, bPersistentLines, Duration, 0, Thickness);
    DrawDebugLine(World, FarBottomLeft, FarTopLeft, FarColor, bPersistentLines, Duration, 0, Thickness);

    // Connect near and far planes with a third color to emphasize 3D shape
    DrawDebugLine(World, NearTopLeft, FarTopLeft, ConnectColor, bPersistentLines, Duration, 0, Thickness);
    DrawDebugLine(World, NearTopRight, FarTopRight, ConnectColor, bPersistentLines, Duration, 0, Thickness);
    DrawDebugLine(World, NearBottomRight, FarBottomRight, ConnectColor, bPersistentLines, Duration, 0, Thickness);
    DrawDebugLine(World, NearBottomLeft, FarBottomLeft, ConnectColor, bPersistentLines, Duration, 0, Thickness);

    // Draw the original forward vector direction
    DrawDebugLine(World, CameraLocation, CameraLocation + Forward * 150.0f, FColor::Red, bPersistentLines, Duration, 0, 4.0f);

    // Draw additional directional indicators
    DrawDebugLine(World, CameraLocation, CameraLocation + Right * 50.0f, FColor::Red, bPersistentLines, Duration, 0, 2.0f);
    DrawDebugLine(World, CameraLocation, CameraLocation + Up * 50.0f, FColor::Red, bPersistentLines, Duration, 0, 2.0f);

    // Draw a sphere at camera position for reference
    DrawDebugSphere(World, CameraLocation, 10.0f, 12, FColor::Red, bPersistentLines, Duration);

    // Log more detailed information for debugging
    UE_LOG(LogTemp, Warning, TEXT("Drew 3D frustum. Camera FOV: %f, Aspect: %f"), FOVAngle, AspectRatio);
    UE_LOG(LogTemp, Warning, TEXT("Near width/height: %f/%f, Far width/height: %f/%f"),
        NearWidth, NearHeight, FarWidth, FarHeight);
}

```