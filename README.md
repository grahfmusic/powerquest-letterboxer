# powerquest-letterboxer
LetterBoxer Fix for PowerQuest/Unity created by Guga (gugames.itch.io)

After a few tries I think I have a stable and mature solution for letterboxing / pillarboxing for PowerQuest games.

It starts with a modified version of the LetterBoxer asset you can find on the Unity store. Why modified? Because PowerQuest uses two cameras, the game cam and the gui cam, and the LetterBoxer component complains if you have more than one. I attach my modified version.

Add this asset to your project and add the LetterBoxer component to both the QuestGuiCamera and the QuestCamera prefabs. Choose the aspect ratio and color, tick both on awake and on update, and tick the Add Extra Camera for only one of the two prefabs.

The second step is to open the SystemTime prefab (in Assets/Game) and add "LetterBoxer" (warning: it's case sensitive!) to the Ignored Components list. This is important so that the LetterBoxer keeps working also when you're, for example, showing the pause gui.

The third step is to fix the savegame screenshots, if you have those. In PowerQuestSave.cs, in the Save function, disable the letterboxer, save the old camera viewport rect, reset it to 0,0,1,1, and after the screenshot has been rendered, reactivate the letterboxer and restore the old viewport rect. I'll post the code in a comment because it's a bit long
