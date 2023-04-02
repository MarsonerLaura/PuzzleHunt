![Banner](https://user-images.githubusercontent.com/104200268/229340363-cde75b30-b776-4727-8847-1ac8496c8db4.png)
<p align="center"><i>PuzzleHunt</i> is a social game for mobile devices that allows players to collect Puzzle Pieces while running around in real life and combine them to complete puzzles. It also allows to gamble at dealers located around the map and to buy puzzlle pieces in shops and to trade them with friends. The longer and better the friendship is the better the trading boni between friends.</p>

<br>

<div align="center">
 
`AndroidStudio`
`Java`
`XML`
`Firebase`
`MongoDB`
`Play! Framework`
`OpenWeatherAPI`
`GitLab`
`Krita`

</div>

---

<p>
<img align="left" width="50%" height="auto" src="https://user-images.githubusercontent.com/104200268/229356173-6fc36fd0-479b-45f7-9951-6359514ab732.jpg">
<h1>About</h1>
<li><b>Role:</b>&emsp;&emsp;&emsp;&emsp;Programmer, Designer</li>
<li><b>Duration:</b>&emsp;&emsp;2 Months</li>
<li><b>Group Size:</b>&emsp;5</li>
<li><b>Genre:</b>&emsp;&emsp;&emsp;&nbsp;Mobile Social Game</li>
<li><b>Platform:</b>&emsp;&emsp;Android</li>
<li><b>Context:</b>&emsp;&emsp;&nbsp;Social Gaming Course</li>
</p>

<br>

<p>
<div>
<img align="right" width="50%" height="auto" src="https://user-images.githubusercontent.com/104200268/229356449-dece401e-a36c-48ed-9296-62fd0eefb1d3.jpg">
<br>
<h1>Responsibilities</h1>
<li>UI Design</li>
<li>Implemented basic functionality of activities</li>
<li>Integration and Usage of OpenWeatherAPI</li>
<li>Leaderboard implementation</li>
<li>Game Design</li>
<li>StoryBoard creation</li>
<li>Icon creation</li>
<br>
<br>
</div>
</p>


<br>

<p>
<div>
<img align="left" width="50%" height="auto" src="https://user-images.githubusercontent.com/104200268/229356456-7ec3ed3f-44f7-4d6f-acb6-a67cff7449d9.jpg">
<br>
<h1>Features</h1>
<li>Collect Puzzle-Pieces</li>
<li>Strengthen Friendships</li>
<li>Shops</li>
<li>Dealers</li>
<li>Leaderboard</li>
<li>Trade Puzzle-Pieces</li>
<li>Weather dependent Puzzle-Piece spawning</li>
</div>
</p>

<br>

---


 <a href="http://www.youtube.com/watch?feature=player_embedded&v=zHgLsDbrP3M
" target="_blank"><img src="https://user-images.githubusercontent.com/104200268/227638337-fd73fd4e-50a8-41b3-9bd4-4d418f4fe416.png" 
alt="Watch Trailer on YouTube" align="right" width="60%" height="auto" border="10" /></a>
<br>
 <br>
  <br>
<div align="center"> Klick on the Image on the right or the button below to watch the Trailer on YouTube! 
<br>
<br>

 
[![Watch Trailer on YouTube](https://img.shields.io/badge/Watch%20Trailer-FF0000?logo=youtube&style=for-the-badge)](http://www.youtube.com/watch?feature=player_embedded&v=zHgLsDbrP3M) 

</div>

<br>
<br>


---

<p>
<h1>Additional Information</h1>
<details>

  <summary>Dialogues & Dialogue Editor</summary>
 
 
  > <details> 
  >  <summary>Dialogues</summary>
  >  <br>
  >  <div align="center">
  >    The players can interact with NPCs by clicking on them, which opens the dialogue window. The conversation starts with the NPC's part, followed by the player's response with multiple answer choices. The dialogues can trigger NPC actions, such as giving quests and NPCs can give random answers. 
  >    Dialogues should enhance immersion while adding a dynamic feeling to the game.
  >   <img src="https://user-images.githubusercontent.com/104200268/227634579-c074e1ef-75a3-4509-9fca-d6fabc0073be.gif" width="60%" height="auto">
  >   </div>
  >  </details>
  
 > <details> 
 >   <summary>Dialogue Editor</summary>
 >
 >   <br>
 >
 >    <div align="center">
 >    The Dialogue Editor also allows developers to create dialogs quickly and efficiently and provides a better overview over the dialogue. Each dialogue consists of several nodes that are connected by Bézier curves.     
 >     <img src="https://user-images.githubusercontent.com/104200268/227770424-3d76d338-f03b-4df5-a914-addf655d198a.png" width="80%" height="auto">
 >     </div>
 >
 >    <br>
 >
 >    <div align="center"> 
 >    Nodes can be added, linked, or deleted, and can also be moved and arranged by dragging them.
 >    <img src="https://user-images.githubusercontent.com/104200268/227791963-3c6d6053-8d6b-49de-ae02-3e3182ebc0c5.gif" width="80%" height="auto">
 >    </div>
 >
 >    <br>
 >
 >    <div align="center">
 >    The Nodes are implemented using scriptable objects. There are different configuration options for the nodes: the size of the text field, selecting whether it is a player or NPC part of the conversation, and adding an Enter or Exit actions. Conditions can be set, such as requiring players to have certain items in their inventory to unlock specific answer options, which is useful for quests and gameplay.
 >    <img src="https://user-images.githubusercontent.com/104200268/227792229-3e894d1e-12cc-48b5-a301-15247fc87b24.png" width="50%" height="auto">
 >      
 >    Triggers can be used to activate actions when a dialog node is entered or exited, such as removing quest items from the player's inventory or giving rewards. The combination of conditions and triggers in dialogs is a powerful tool for driving the story and gameplay. 
 > </div>
 >   
 > <br>
 >
 > </details>
 
 > <details> 
 >  <summary>Code Snippets</summary>
 >  <br>
 >    Creation of an Editor Window
 >
 > ```c#
 > [MenuItem("Window/Dialogue Editor")]
 > public static void ShowEditorWindow()
 > {
 >     GetWindow(typeof(DialogueEditor), false, "Dialogue Editor");
 > }
 > ```
 > <br>
 >    This Method draws the Bezier Curves to connect the dialogue nodes.
 >
 > ```csharp
 > private void DrawConnections(DialogueNode node)
 > {
 >     Vector3 startPosition = new Vector3(node.GetRect().xMax, node.GetRect().center.y,0);
 >     foreach (DialogueNode childNode in _selectedDialogue.GetAllChildren(node))
 >     {
 >         Vector3 endPosition = new Vector3(childNode.GetRect().xMin, childNode.GetRect().center.y,0);
 >         Vector3 controlPointOffset = endPosition - startPosition;
 >         controlPointOffset.y = 0;
 >         controlPointOffset.x *= 0.9f;
 >         Handles.DrawBezier(startPosition, endPosition, startPosition + controlPointOffset, 
 >           endPosition - controlPointOffset, Color.white, null, 4f);
 >     }
 > }
 > ```
 > <br>
 >    This Method is called if a Dialogue Scriptable object is opened and automatically opens the Dialogue Editor.
 >
 > ```csharp
 > [OnOpenAsset(1)]
 > public static bool OpenDialogue(int instanceID, int line)
 > {
 >     Dialogue dialogue = EditorUtility.InstanceIDToObject(instanceID) as Dialogue;  
 >     if (dialogue != null)
 >     {
 >         ShowEditorWindow();
 >         _selectedDialogue = dialogue;
 >         return true;
 >     }
 >     return false;
 > }
 > ```
 ><br>
 >
 >    This Code only works in the Editor Mode and displays how nodes are created and deleted.
 >
 > ```csharp
 > #if UNITY_EDITOR
 >   public void CreateNode(DialogueNode parent)
 >   {
 >       DialogueNode child = MakeNode(parent);
 >       Undo.RegisterCreatedObjectUndo(child, "Created Dialogue Node");
 >       if (AssetDatabase.GetAssetPath(this) != "")
 >       {
 >           Undo.RecordObject(this, "Added Dialogue Node");
 >       }       
 >       AddNode(child);
 >   }
 >       
 >   public void DeleteNode(DialogueNode nodeToDelete)
 >   {
 >       Undo.RecordObject(this, "Removed Dialogue Node");
 >       nodes.Remove(nodeToDelete);
 >       CleanDeletedChildren(nodeToDelete);
 >       OnValidate();
 >       Undo.DestroyObjectImmediate(nodeToDelete);
 >   }
 >
 >   private DialogueNode MakeNode(DialogueNode parent)
 >   {
 >       DialogueNode child = CreateInstance<DialogueNode>();
 >       child.name = Guid.NewGuid().ToString();
 >       if (parent != null)
 >       {
 >           parent.AddChild(child.name);
 >           child.SetPlayerSpeaking(!parent.IsPlayerSpeaking());
 >           child.SetPosition(parent.GetRect().position + newNodeOffset);
 >       }
 >       return child;
 >   }
 >
 >   private void AddNode(DialogueNode child)
 >   {
 >       nodes.Add(child);
 >       OnValidate();
 >   }
 >       
 >   private void CleanDeletedChildren(DialogueNode nodeToDelete)
 >   {
 >       foreach (DialogueNode node in GetAllNodes())
 >       {
 >           node.RemoveChild(nodeToDelete.name);
 >       }
 >   }
 > #endif
 > ```
 >
 > </details>

</details>

 <details>
  <summary>Thesis</summary>
 <br>
  
  > <div align="center"> 
  >  If you are interested in obtaining more information, you can download the final presentation and the bachelor's thesis using the links provided below. These resources contain valuable insights and details about the project.
  > <br>
  > <br>
  >
  > [Presentation.pdf](https://github.com/MarsonerLaura/KingdomOfMath/files/11094274/BA.Prasentation.pptx.pdf)
  > <br>
  >
  > [Thesis.pdf](https://github.com/MarsonerLaura/KingdomOfMath/files/11094238/Thesis.pdf)
  > <br>
  > <br>
  > Abstract
  > <br>
  > Serious games have shown promise as a tool to enhance the learning experience by generating higher intrinsic motivation than traditional learning methods. In this paper, a serious game called Kingdom of Math is developed that aims to teach mathematics to secondary school students using proven design principles. To this end, essential terms and concepts are described, and related work is analyzed. The requirements for such a serious game are outlined, and the approach and design decisions made are discussed and implemented. A user study is conducted to evaluate the developed game, and the results are presented and discussed. In addition, possible improvements and enhancements for this project in the future are suggested.
  > </div>
  > <br>
> 
   
</details>
 
</p>
