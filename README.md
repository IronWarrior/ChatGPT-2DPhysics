This repository contains a simple 2D Physics engine in C#, with code written by ChatGPT. It uses the console for graphics.

![GPTPhysics](https://user-images.githubusercontent.com/12469377/205753410-030bd615-3084-4ae1-ae3b-40eee32477dc.gif)

ChatGPT describes itself as:
> I am a large language model trained by OpenAI. I generate human-like text based on input.

The code was generated by a large series of prompts. You can find the entire log in [`prompt-log.md`](prompt-log.md). I made two modifications to the generated code after completing the session; these are noted in the header comment in [`Program.cs`](Program.cs).

## Workarounds

ChatGPT's output has a maximum character limit. Sometimes this results in code snippets being cut off halfway. To avoid this, I primed the bot with the following command:

> combine all of the necessary code to create a physics engine into a single C# file. Start printing the file out. Due to your text limitation, printing out the entire code for me will take many steps. When I prompt you with "continue", your next response should ONLY contain the next segment of the file. If the final line of code was not written out completely in the previous response, start your next response including that line of code in its entirety.

And then manually joined the segmented blocks of code. 

## Remarks

My approach was to instruct ChatGPT to build out the program in a piecemeal way. I typically would ask it to create some boilerplate code first, and then to fill in the gaps. For example, the second prompt is:

> okay, let's do it together. It will use C# language. Write out the boilerplate code to get us started

Which returns:

```cs
// Define a class for a 2D physics object
class PhysicsObject
{
    // Position, velocity, and acceleration vectors
    Vector2 position;
    Vector2 velocity;
    Vector2 acceleration;

    // Mass of the object
    float mass;

    // Constructor for a new physics object
    public PhysicsObject(Vector2 pos, Vector2 vel, Vector2 accel, float m)
    {
        position = pos;
        velocity = vel;
        acceleration = accel;
        mass = m;
    }
}

// Define a class for a 2D physics engine
class PhysicsEngine
{
    // List of physics objects in the engine
    List<PhysicsObject> objects;

    // Constructor for a new physics engine
    public PhysicsEngine()
    {
        objects = new List<PhysicsObject>();
    }

    // Method to update the state of the engine
    public void Update()
    {
        // TODO: Implement physics update code here
    }
}
```
My experience was that this often felt more like a master-pupil relationship, rather than between a worker and an assistant. This may be due to my approach of requesting it to build the code up piece by piece (and correcting for errors I spot). As well, ChatGPT's success here is in part due to my prexisting domain knowledge of physics engines, allowing me to spot errors as they arrive.

Often the changes I had to request were fairly small, making the commands feel less like an interaction with an intelligent agent and more like performing non-deterministic compilation of plain english into C# code. Some of these issues, like missing required explicit casts, would be easily resolved if the AI were capable of interacting with an actual C# compiler.
