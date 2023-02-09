# Velocity-Controller

Velocity Controllers allow for complex behaviour to arise from blending 'Velocity Overrides'.
Velocity Overrides can be animated over their lifetime and chained together using the onComplete callback.

#Example

simple 3D character controller:
```csharp
[SerializeField] private VelocityController vc;
[SerializeField] private float jumpVelocity = 15f

[...]
void FixedUpdate() {
  var clearChannelMask = Grounded ? VelocityChannelMask.XYZ : VelocityChannelMask.XZ;  
  vc.AddOverwriteMovement(new(movementInput, speed, VelocityBlendMode.Overwrite, VelocityChannelMask.XZ), 0f, 0);
  vc.AddOverwriteMovement(new(Vector3.up, jumpVelocity, VelocityBlendMode.Overwrite), 0f, 0);
}
```


