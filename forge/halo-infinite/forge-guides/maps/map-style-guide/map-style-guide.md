# Halo Infinite Map Style Guide

*"Simplicity, as a pillar, is here to make sure we do a sanity check on decluttering and readability at all levels."* - **Halo Art Index**

## What is the fidelity bar for Halo Infinite Forge maps?

Overall map visual quality relies a great deal upon the underlying quality of the objects used. Halo Infinite's Forge has a robust library of high quality assets; materials, decals, and textures, built to rigid standards. By maximizing reuse, employing standards of composition, maintaining consistency, and only adding high fidelity to key spaces, you can create high quality Forge map experiences. Below are guidelines of best practices to achieve an acceptable level of fidelity for Halo Live Maps. Further down, there are specific test-cases that use existing maps as examples.

###### Add Ons and Decals

![](C:\Users\mischorr\Documents\GitHub\forge-docs\forge\halo-infinite\forge-guides\maps\map-style-guide\media\addons-decals-01.png)

![](C:\Users\mischorr\Documents\GitHub\forge-docs\forge\halo-infinite\forge-guides\maps\map-style-guide\media\addons-decals-02.png)Add Ons are props that you can stamp on surfaces to provide small pockets of detail.  They can help to quickly finish out areas.

Decals provide color, detail, and readability around doorways and other key areas. For floors especially, decals can provide the majority of the detail/polish.

Leverage details with intent

###### Gobos and FX

![](C:\Users\mischorr\Documents\GitHub\forge-docs\forge\halo-infinite\forge-guides\maps\map-style-guide\media\gobos-fx-01.png)

![](C:\Users\mischorr\Documents\GitHub\forge-docs\forge\halo-infinite\forge-guides\maps\map-style-guide\media\gobos-fx-02.png)

- Gobos and shadows can be used to bring spaces to a finished state. Spaces like this require fewer additional detail solutions.
- Liberal use of FX (with deference to good game design) are vital to spaces feeling polished.

###### Color as Detail

![](C:\Users\mischorr\Documents\GitHub\forge-docs\forge\halo-infinite\forge-guides\maps\map-style-guide\media\color-as-detail-01.png)

![](C:\Users\mischorr\Documents\GitHub\forge-docs\forge\halo-infinite\forge-guides\maps\map-style-guide\media\color-as-detail-02.png)

- Simply adding color breakup more frequently in levels can help the map feel crafted, intentional, and more detailed.
- Liberal use of color to improve readability, mark important areas, and guide players is key.

###### Focusing Fidelity

![](C:\Users\mischorr\Documents\GitHub\forge-docs\forge\halo-infinite\forge-guides\maps\map-style-guide\media\focusing-fidelity-01.png)

- Confine expensive set dressing to hero pieces, or pre-defined objective areas.
- 1 to 2 per map, maximum
- Let passthroughs be passthroughs.
- Frame custom areas in simplicity.
- Ask yourself:
  - Where do people travel?
  - What is important information to convey to the player?
- Focus details around objectives and around where players spend their time.

###### Materials over Geometry

- Rely on materials to sell detail - geo is nice, but not always necessary
- Decals and blending on floors and walls can add detail to scenes.
- More frequent material mixes can add detail to scenes.
- Reflective surfaces can add detail to scenes.

A map doesn't need to incorporate all these elements, just enough of them to sell the space. 

### Test Cases

###### 1 - "How finished are these spaces?"

These are two examples that would be considered 90% complete, with only one major note below to call them finished.

![](C:\Users\mischorr\Documents\GitHub\forge-docs\forge\halo-infinite\forge-guides\maps\map-style-guide\media\testcases-howfinished-01.png)

![](C:\Users\mischorr\Documents\GitHub\forge-docs\forge\halo-infinite\forge-guides\maps\map-style-guide\media\testcases-howfinished-02.png)

| Pass                                                                                            | Fail                                                     |
|:----------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| Decals provide detail and polish                                                                | Tiling textures on floor need blending or decal breakups |
| Addons provide details to otherwise simple walls, and are focused on doorways/areas of interest |                                                          |
| Addons provide details to otherwise simple walls, and are focused on doorways/areas of interest |                                                          |

###### 2 - Terrain Transitions

![](C:\Users\mischorr\Documents\GitHub\forge-docs\forge\halo-infinite\forge-guides\maps\map-style-guide\media\terrain-transitions-01.png)

![](C:\Users\mischorr\Documents\GitHub\forge-docs\forge\halo-infinite\forge-guides\maps\map-style-guide\media\terrain-transitions-02.png)

![](C:\Users\mischorr\Documents\GitHub\forge-docs\forge\halo-infinite\forge-guides\maps\map-style-guide\media\terrain-transitions-03.png)

![](C:\Users\mischorr\Documents\GitHub\forge-docs\forge\halo-infinite\forge-guides\maps\map-style-guide\media\terrain-transitions-04.png)

| Pass                                                                                                                                                | Fail                                                                          |
| --------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| Image 2: Soft transitions in all cases between terrain and objects, both manmade and organic. Image 2 is an example of acceptable finished quality. | Image 1: Harsh, flat transitions with no blending or meshes to break up lines |
| Image 2: High quality texture blending                                                                                                              | Image 3: Harsh color transitions should be avoided.                           |
|                                                                                                                                                     | Image 4: Needs some mesh breakup at the transition. Looks rushed.             |
|                                                                                                                                                     | Inconsistent map-wide approach to transitions.                                |

#### 3 - Simple Success

These examples in Ridgeline use 'just enough' detail to sell the scene. Minimal mesh detailing in passthroughs and care given to transitions help make this feel complete.

![](C:\Users\mischorr\Documents\GitHub\forge-docs\forge\halo-infinite\forge-guides\maps\map-style-guide\media\simple-success-01.png)

![](C:\Users\mischorr\Documents\GitHub\forge-docs\forge\halo-infinite\forge-guides\maps\map-style-guide\media\simple-success-02.png)

| Pass                                                                                  | Fail                                                                           |
| ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| Simple, reusable walls                                                                | No fails, but some mesh cut-ins in floors may be excessive if they were custom |
| Transitions look polished and soft, with just enough mesh breakup to provide fidelity |                                                                                |
| Good overall breakup on floors using material variance                                |                                                                                |
| Large details provide detail and interest                                             |                                                                                |
