# UE_Shaders
Technical art shaders project using Unreal Engine.

## 1. Stylized Water Material with World Position Offset

- How does WPO affect performance compared to animated meshes?
- How can you control wave direction and intensity?
- What vertex density is required for smooth wave deformation?
- How does your water material respond to different lighting conditions?

## 2. Material Parameter Collection (MPC) System

- Why use MPC instead of individual material parameters?
- How does your system maintain visual consistency across materials?
- What performance benefits does MPC provide?

## 3. Dynamic Material Instance with Runtime Control

- When should you use DMI versus Material Instance Constant?
- How do you optimize DMI creation and updates?
- What gameplay scenarios benefit from runtime material modification?

## 4. Parallax Occlusion Mapping (POM) Material

- How does step count affect visual quality and performance?
- What types of surfaces benefit most from POM?
- How does POM compare to simple bump offset?
- What are the limitations at silhouette edges?

## 5. Post Process Material

I decided to make a drunk first person shader.

1. Started with a screen position node with UV plugged into a SceneTexture node plugged into the result node. I experimented with adding random operations into this setup to observe the effects, for example, multiplying UVs, adding sine nodes, adding to UVs.

2. Added add noise texture to add to add to the UV to produce a blurring effect. I divided the scale parameter to ensure that the values would not be too small when configuring its material instances.

3. Wanted the screen to stretch from the center but I ran into a problem where the stretching would occur from the edge instead. After some research, I learned that in order to stretch from the center you must first move the UVs center to the origin position, stretch, then move the center back.  
Wanted to have the u and v axes to stretch in an unsynced sinusoidal manner so I used two component masks for u and v, stretched the values, then appended it back together. To cause the unsynced stretching, I used sine for the u and cosine for the v. All this takes place inbetween the center movement and restoration.

4. Wanted the screen to rotate back and forth to simulate the poor coordination and disorientation while drunk. Chose to use a custom rotator node as it was straightforward, then applied a rotation using sine and time nodes. Made a rotation angle parameter but I did not like how the angle goes from 0 to 1 so I divided it by 360 to make it more intuitive to someone configuring the material instance.

5. Wanted a tinge applied to be applied fullscreen. Multiplied the scene texture's color output by a color but ran into a problem, the color was not accepted because of a vector type difference. I did not realise that the white output pin of my color does not include alpha, meaning it was a vector 3, when I needed a vector 4. Solved by appending the alpha channel to RGB.


## Assessment Criteria

Your work will be evaluated against the following criteria:

### Exploring
- Engaging in critical and creative inquiry through questioning, research, and material/process-based investigations
- Demonstrating understanding of technical concepts through implementation
- Experimenting with parameters and techniques to understand their effects

### Making
- Developing and refining creative work through iteration, risk-taking, and material engagement
- Technical proficiency in material creation and Blueprint implementation
- Quality of visual output and attention to detail
- Problem-solving when encountering technical challenges

### Connecting
- Communicating technical decisions and implementation choices
- Engaging with professional workflows and industry-standard practices
- Demonstrating understanding of when and why to use specific techniques
- Clear documentation of your materials and systems

### Situating
- Critically positioning work within professional game development contexts
- Understanding performance implications and optimization considerations
- Awareness of platform limitations and scalability
- Ethical consideration of accessibility (e.g., motion, visual effects)

### Synthesizing
- Bringing together disparate elements into meaningful, cohesive outcomes
- Creating a unified showcase that demonstrates multiple techniques working together
- Integrating materials into a coherent scene or demonstration
- Showing how different systems complement each other

---


**Technical Documentation** 
   - Brief description of each deliverable
   - Technical challenges encountered and solutions
   - Performance considerations and optimization choices
   - Reflection on learning outcomes and professional applications
   - Include screenshots, gifs and any other applicable media
   - Show before / after where relevant
   - Detail your understanding of your implementation


---


### Documentation:
- Take screenshots of your material graphs as you work
- Record video clips of interesting developments
- Note down problems and solutions as they occur
- Explain *why* you made specific technical choices

---


**Remember:** This task is about demonstrating technical understanding through practical application. Focus on clean implementation, good documentation, and showing that you understand *why* these techniques are used in professional workflows.

<br>

<br>

<br>

html spans

desmos

<span style="color:red">This text is red.</span>  

<span style="color:blue">This text is blue.</span>  
<span style="color:cyan">This text is cyan.</span>  
<span style="color:teal">This text is teal.</span>  
<span style="color:turquoise">This text is turquoise.</span>  
<span style="color:lightblue">This text is light blue.</span>  
<span style="color:azure">This text is light blue.</span>  

<span style="color:green">This text is green.</span>  
<span style="color:lightgreen">This text is light green.</span>  

<span style="color:orange">This text is orange.</span>  

<span style="color:purple">This text is purple.</span>  

