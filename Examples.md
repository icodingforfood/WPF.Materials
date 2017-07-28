# Usage

Using `AcrylicContainer` is quite simple. It behaves just like a `Border` control, but require a couple of small steps to set up.

### Rules and Requirements
- The `AcrylicContainer` cannot be in the same lineage as the RootPanel it will "blur". Setting up a pseudo-root object as shown in the example below is recommended.
- The RootPanel object (generally a container or panel) must be specified. This can be done by code or by binding.
- Use the AcrylicContainer sparingly. It can be resource-hungry, especially on older GPUs.

### Example
```XAML
<Window>
    <Grid> <!-- root element -->
        <Grid x:Name="grid"> <!-- psuedo-root element which will be blured -->
            <Grid.Background>
                <!-- An image is not required, but looks pretty cool! -->
                <ImageBrush ImageSource="Poster-001.jpg" Stretch="UniformToFill" />
            </Grid.Background>
            <!-- all your normal content and controls should go here -->
        </Grid>

        <!-- AcrylicContainers should be declared at the "sibling" level of the pseudo-root -->
        <materials:AcrylicContainer Margin="300" RootPanel="{Binding ElementName=grid}">
            <!-- Add your content inside the AcrylicContainer -->
            <Grid>
                <Button Margin="52,46,0,0"
                        VerticalAlignment="Top"
                        HorizontalContentAlignment="Left"
                        Content="I'm a button!" />
            </Grid>
        </materials:AcrylicContainer>
    </Grid>
</Window>
```
