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
  var movementInput = new Vector3(Input.GetAxisRaw("Horizontal"), 0, Input.GetAxisRaw("Vertical"));
  movementInput = Quaternion.Euler(0, Camera.main.transform.eulerAngles.y, 0) * movementInput; //rotate input to convert to camera local
  vc.AddOverwriteMovement(new(movementInput, speed, VelocityBlendMode.Overwrite, VelocityChannelMask.XZ), 0f, 0); //Only affects the XZ plane
  vc.AddOverwriteMovement(new(Vector3.up, jumpVelocity, VelocityBlendMode.Overwrite, VelocityChannelMask.Y), 0f, 0); //Only affects the Y axis
}
```


