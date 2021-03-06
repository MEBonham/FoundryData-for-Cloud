# Sandbox

Build any system, without coding a single line in Javascript.

## Important

This system has been developed by me, Seregras (IsmaGM), after extensive hours of brain damage caused by thinking too much. If you like this system, please consider helping me promote ttrpgs in Spanish speaking countries by subscribing to my Youtube/Twitch channels below, or sharing them on social networks. Please consider helping me even if you don't speak Spanish, because I really want my favourite hobby to be generally seen in Spain & Latinamerica as it is actually seen in English speaking countries:

[Rol NL - Youtube](https://www.youtube.com/c/RolNL)

[Rol NL - Twitch](https://www.twitch.tv/rolnl)

Also, consider donating if you want to help me, I will have to work a lot if we want to improve this:

[Rol NL - Donate](https://streamlabs.com/rolnl/tip)

## Disclaimer
I am not a programmer. I am just a poor chemical engineer, and a big fan of ttrpgs. So yes, the code might look like Chaos (which is fine, I am a Tzeench follower myself). It might be difficult to understand why I structured things this way, and there might be a better way of organising it, I know. Just bear with me, if you tell me how and help me, we can all get a great version of Sandbox. If you need clarification, just ask me, I am @Seregras in the Foundry discord channel.

## Tutorials
Playlist with videotutorials in English (if there aren't any, wait some days, I will try to upload every fortnite)
[Videotutorials -English](https://www.youtube.com/playlist?list=PLMAQsyqo9jDFpHYy4WZv0eF_SgqotcUKs)

Playlist with videotutorials in Spanish (why not? You might learn some)
[Videotutorials -Spanish](https://www.youtube.com/playlist?list=PLMAQsyqo9jDFEfeqRHBhwHT7kY_1eK2zY)

Do you have questions? Join my discord server and head to SANDBOX ENGLISH, I will help you there!
[Discord](https://discord.gg/QE7CHNP)

## Frequent issues
- Do not insert data in the Template actor. Template Actors are not for sheet building, just create regular actors for that!
- After rebuilding a sheet, any previous character will require changing its sheet to Default, and back again to the current sheet, in order to display the new changes
- Never forget to include a key to a Sandbox element, or it won't let you drag it anywhere. Also, make sure keys are unique and do not contain spaces!

## Index
1. Basic Sheet Structure
2. Creating Properties
3. Advanced Panels & Tabs
4. Groups & cItems
5. Tables
6. Modifiers (MODs)
7. Roll Expressions
8. Folder structure best practices

## 1.Basic Sheet Structure
So you want to create your favourite ttrpg on Foundry to play online? Uh, let's see what we can do to help you. First, you need an idea of your character sheet, a sketch would do, something simple on a piece of paper. Lets assume we want something like this:

![Sketch](docs/images/tuto1.png)

Now we have to decide how many tabs we will include in our Sandbox character sheet. Tabs are located here:

![Tabs](docs/images/tuto2.png)

So let's say we need 2 tabs, one for the character stats, and one for the inventory. Now, we have to decide how many panels we need. Panels are sections of the character sheet that contain properties, or basically the input fields that we can edit on a sheet. Panels need a width, and is relative to the maximum width of the sheet: 1,2/3,1/2,1/3,etc. So in our case, we are going to build 4 panels:

[Rearranging Tabs & Panels](docs/images/tuto3.png)

Now that we have an idea about how to structure our character sheet on Sandbox, we can start the real fun. First, we need an element that will store the structure of our character sheet, and this is called Template Actor. We can create one by creating a new actor, and then checking the "Template" box. Let's call it _templateActor_pc:

![Creating a Template Actor](docs/images/tuto4.png)

Be careful not to delete your Template Actor by accident! Try to have it stored in a safe Folder within the actors sidebar.

With a Template Actor ready, we just need to add to it the tabs, panels, and properties we need. Let's start with the tabs. Go to Items Directory and create a new Item, select the type as "sheettab" and name it "Stats Tab" for example. You can name it as you like:

![Creating a Tab](docs/images/tuto5.png)

Every Tab has three tabs (that was funny):
- Description: Here you can write a description of the tab's function, or an explanation. Something for the rest of us to understand it's intention.
- Details: Here you must fill the Title, with the name that will be displayed on the sheet, and the Key. A Key is a unique name that every element in Sandbox will have, from Tabs, to Panels, to Groups... every element. A Key must not have any spaces, and must be unique, if not... the army of darkness will spawn from your screen.
- Panels: Here we will drag and drop the panels that the tab will contain.

Your tab should look like this:

![Editing Tab](docs/images/tuto6.png)

So, there is your first Tab. Now, let's add it to our Template Actor. Open the Template Actor, open the Tabs tab (haha, always get's me), and drag the recently created Tab from the Items Directory onto the Template Actor. You will see something like this:

![Adding tab to Template Actor](docs/images/tuto7.png)

Our Template Actor has now it's first Tab, but is not ready to be used by the system. For that, you just need to press "Rebuild Sheet" and press F5. Very Important, you need to press F5 every time you rebuild a Template Actor!

So, once everything has reloaded, we are ready to check our custom character sheet. Create a new Actor, name it as you like, and then assign it a template actor sheet. You will see, but by default, every newly created actor has Default template assigned. The Default template creates 2 tabs, Bio (where you can write the biography of the character) and cItems (where you can see the list of cItems, will talk later about this). So once we select our template sheet, which is named after our Template Actor, the Actor sheet changes:

![Setting a template sheet on an Actor](docs/images/tuto8.png)

And voila! our character sheet with the new Tab "Stats" has been created. But is empty... So now it's time to create Panels and properties. So delete this abomination of Actor and let's go back to our Template Actor.

Ok, Panels, so click on create a New Item on the Items Directory, and select "panel". Name it something like "Main Info Panel", or "Super Duper Awesome First Panel", whichever you like. A Panel has the same tabs than a Tab, so let's go straight to the Detail tab. As always, we need to fill the Key, but in this case the Panel title is not that important, so we will leave it blank. If Sandbox sees that a panel has no title, it won't draw a title header:

![Create a Panel](docs/images/tuto9.png)

Now, we need a width. If you remember our sheet sketch the first panel has a width of 1 (it occupies all the width of the sheet) and has 3 properties: Level, Race, Class. As it has 3 properties on the same row, that equals to 3 columns. So select Width:1 and Columns:3. You can also choose the alignment of the elements inside the panel,  and the alignment of the property labels inside it. Leave it as "left" for both of them, but you can experiment later if you want.

With our first panel ready, it's time to add some real content to our sheet, let's create some properties.  A property is an element within a character sheet that creates an attribute of a specific type. The attribute stores a value and a key. For example, if we create the property "Level" of the type "simplenumeric" and key "level", any Actor of this character template will have the attribute "level", and it will be a number. So let's create it! Create an item on the Items Directory. Choose "property" and name it "Level". Properties have a lot of fields, and will be explained on the next section, but for now set it up like this:

![Create a Property](docs/images/tuto10.png)

So basically, we are telling Sandbox that Level is a property that, after been attached to an actor's sheet, will create the attribute "level", which is a number, and it's default value will be 1. We are also specifying that it will be visible (Hidden is not checked), that the player won't be able to edit it (Editable is not checked), and that it will display a label next to it, and that the text of this label will be "Level".

If we go back to our Panel, and we drag the Property element we just created into it (from the Item Directory), we would have our first property set in a Panel. Then drag the Panel (from the Item Directory) in to our Stats Tab:

![Adding a Property to a Panel](docs/images/tuto11.png)

So let's go back to the Template Actor, and rebuild it's sheet. Remember to hit F5 right after. Let's create a new minion... sorry, Actor! If we set it's character template to our Template Actor, and then click on Stats tab we can see how our character sheet looks like with one tab, one panel, and one property!

![First Property on a character Sheet](docs/images/tuto12.png)

Awesome! It even has the default value of 1 we set previously!

So, to summarize, Sandbox is based on Template Actors. Template Actors store the structure of a character sheet, mainly tabs, panels and properties. When we create a regular Actor, we assign it a Template Actor, from which to draw the character sheet. This way you can have Template Actors for PCs, NPCs, Loot Windows, etc, all in the same world.

## 2.Creating Properties
There are 9 types of properties: simpletext, simplenumeric, checkbox, radio, textarea, list, label, badge, table. Properties generate an attribute on an Actor, when said Actor is assigned a Template Actor character sheet with that Property. All the Properties listed (except table) have a very similar way of setting them up. Let's go through the Properties window options:

![Setting up Properties](docs/images/tuto13.png)

- Key: the unique identifier of the property's attribute. Remember, never leave it blank, I haven't had the time to include an auto naming tool for it. And very important, again... no space!! Try things like "strength_mod", "sanity_level", "hunger_rating", etc.
- Default Value: whenever you create an Actor with this property on it's template sheet, this is the value that will be desplayed initially. Be careful, if you set up a simplenumeric don't set a word as default value, the system can't check that right now. Also, when setting booleans, use false and true (no capital letters).
- Data Type: one of the data types liste above.
- Editable: if checked, players will be able to edit this field on their character sheets. If not, only GM will be able to.
- Hidden: if checked, this property will still create an attribute with name equal to Key in the character, but won't be shown on the character sheet. To anyone, not even the GM.
- Has Label?: if checked, to the left of the input field generated by this property a text will appear. For example "Level" in our previous example.
- Tag: The text of the label. Yeah, I probably should have named it label text...
- Label Size: if the property has a label, this field states the width. If you keep it as "Fit", it will autosize to the length of the text. If you are going to create many rows of properties, let's say for example the typical attributes from D&D (STR,DEX,CON,etc), it's better for you to use Small or Medium, so all of them end up aligned.
- Label Format: Normal is just... normal haha... ok. Bold is... Small means that the font is slightly smaller, it's useful if you don't have much space for the label. And Die removes the label and inserts an icon of a d20. Useful if you want to create Label Properties on sheets to roll dice, whether it's on sheets or cItems.
- Rollable: When checked, the roll confiruation input fields will be shown (Roll Name, Roll ID, Roll Formula). This will be explained later, section 7 Roll Expressions.
- Max Value: If radio, it sets the maximum circle radio buttons to be displayed (radio buttons like in the Vampire the Masquerade character sheets). If simplenumeric, filling this input field would display a box with the max value on the right side of the input. For example, if we create a property called Hit Points (HP, PG in Spanish) and set Max Value as 10 and Default Value as 10:

![Max Value Property](docs/images/tuto14.png)

 Max Value also accepts formulas and roll expressions.

- Auto: Only for simplenumeric or radio. It sets the value of the attribute of the property as the result of the expression introduced. For example, if you write 10+2, the result will be 12, and always be, it can't be edited even by the GM. It accepts roll expressions, like @{level}+2 (see section 7).
- Options (a,b,c): Only for list type properties. Separate the options you want displayed on the list box by commas (don't include the space after the comma);

Experiment a bit with them and panel positions until you are comfortable with basic character data design in Sandbox.

## 3.Advanced Panels & Tabs
Now, imagine that for your ttrpg you set up a Tab called Magic Spells, and of course you only want it visible to characters that are magic users. How could you do that? Well, if you open the Tab you will see the following option at the bottom called VISIBLE IF:

![Tab and panel visibility](docs/images/tuto15.png)

So basically it checks if an attribute meets a specific condition, and if it does it makes the panel/tab visible. So you could create a property with the hidden trait and set it through other means, in order to hide/display the aforementioned Magic Tab.

Also, if you want to group panels vertically you can use Multipanels. You can create it from the Items Directory, by Create Item option and selecting "multipanel". A Multipanel displays a number of panels in a vertical layout group. You can use it as a de facto panel, and add it to a tab:

![Multipanels](docs/images/tuto15a.png)

## 4.Group & cItems
You are still here? Wow, you are hardcore. Ok then let me introduce you to the fantastic world of cItems. It stantds for Compendium Items, but as Foundry already calls Compendium to something else... cItems will do. Basicaly these are all the elements in the rules system that will interact with the character sheet. How? Of course, by dragging them on to Actors. Some examples of cItems can be: 
- An object, let's say a Backpack. With attributes like weight, capacity, etc.
- A weapon, with attributes like damage, range, etc.
- A trait, like "Darkvision" or "Sneak Attack" or "Fey Ancestries".

So in essence, a cItem is anything that can modify an Actor. And you can decide what exactly makes the cItem and how it modifies the Actor. Yep, now you start to think that this Sandbox thing might be more than what you thought...

So how can we create a cItem? Go to Items Directory and create an element with the cItem type:

![Creating a cItem](docs/images/tuto16.png)

You will see the following tabs on a cItem:
- Info: you can write here the info of the item. For example if it was a Sword somtehing like "Swords are very popular weapons made of steel that bla bla bla"
- Attributes: here you will find the attributes of the cItem. Attributes are always created by Properties, as seen before, but... where to put your property on a cItem? Hah, my friend you will have to wait a bit more.
- Groups: 90% of the cItems you will create will have a group. The other 10% will be incorrect. A group sets the common properties and behaviour that a pool of cItems has. For example, you could create a "Weapon" group and add it to the items Sword, Axe, and Dagger. Or create the "Trait" group and add it to "Darkvision", "Fey Ancestries", and "Sneak Attack" cItems. On this tab is where you can drag and drop groups. A cItem can have more than one group.
- MODs: This is necromancy for you right now... wait a bit more.

So let's create a group for our Sword cItem. Go to the Item Directory and create a Group called "Object":

![Creating a Group](docs/images/tuto17.png)

You will see the following tabs on a Group:
- Description: you can write here a description for the group. This will be mainly info for the GM, for reference, as a player will never encounter a group definition.
- Details: her you MUST define the group key (remember to follow the previous instructions), and ou can specify a unique group. What is that? Well, imagine you have a group called "Race", and you create a couple of cItems with that group attached: "Elf" and "Dwarf". Now, if you drag the "Elf" cItem onto an Actor it will become an elf (and I am sorry for you, I hate elves). So imagine you drag the "Dwarf" cItem next onto the same Actor. If the "Race" group has the Unique option checked, the Dwarf cItem will kick  the Elf cItem back to its stinky forest, because cItems of a Unique group can't have other fellow cItems of the same group under the same Actor. But if Unique is not checked, the Actor will be both Dwarf and Elf, and that is... weird.
-Properties: Aha! Here you can add the Properties to a Group, so when you add a group to a cItem the attribute will be created. Unlike on Actors, group's properties can be constant or variable. If they are constant the will never change. For example, the Weight property of a sword will always be the same, thus it has to be constant. On the other hand, in your system you could have armor that loses Protection points each time it is used, so in this case the Property "Protection" of the "Armor" group would not be constant.

In our example, we are creating the Object group, wchich is not going to be unique (as you can have many different cItems of the Object group in any Actor). We are going to create a Property called Weight, with Key:weight and simplenumeric type, and drag it to the group, and make it constant:

![Adding properties to a Group](docs/images/tuto18.png)

Now, let's create a similar group, called "Weapon" and let's add a Property called "Damage" to it, with Key:damage and simpletext type, and also constant:

![Creating more groups](docs/images/tuto19.png)

So time to get back to our previously created Sword cItem. Now, drag the groups Object and Weapon onto it (from the Items Directory), and behold the magic! If you open the Attributes tab on the cItem, you will see the attributes created... and you will be able to set them! So for this Sword we set Weight 2 and damage 1d6!

![Adding groups to a cItem](docs/images/tuto20.png)

I know what you are thinking... and you guessed right. This way, you can create whole rulesets and compendiums. Imagine you create the "Dwarf" cItem with the "Race" group, and when you drag it onto an Actor, it automatically adds it the "Darkvision" trait cItem and increases its Constitution attribute by 2... imagine... is that possible in Sandbox? Of course. But let's continue with something else first... cItems are only displayed on Tables inside an Actor sheet, let's learn about them.

## 5.Tables
I forgot to tell you someghing important, the only Property element different than the rest is Table. In fact, it shouldn't be a Property, but hey I realised that very late and didn't know where to put it. But let's leave it there just in case. 

So a table will display all cItems inside an Actor of a specific group. The table will display each property of the group as a column (if said property is not Hidden). So let's create then an Inventory table in our example character sheet. We already have an Object group created so this table will display all cItems of the group Object contained in the Actor. Let's create it:

![Creating a Table](docs/images/tuto21.png)

So when you choose table as the Data Type, everything changes on the property menu, and you find the following NEW options:
- Group: Here you have to drag and drop a Group from the Items Directory. For this example, just drag the newly created Object group.
- Editable: if you check this option, the player will be able to delete rows of the table
- Has Header?: The table will display a Header with the names of the columns
- Height: The maximum height of the table. Free works fine XD
- Item Names: if unchecked the table will hide the first column, which is the name of the cItems. Why would this be useful? Simple, imagine you want custom elements in your table, and you want to name them on the fly, and when they are whosn on the table. Simply add a "Name" property to the cItem's group and make it variable, so you can rename the item whenever you want. However, this is a fake name property, the cItem will always have it's original name. This is specially useful when you want to create custom attacks for example. Let's say you create Attack 1, Attack 2, Attack 3, and you create fake "name" properties for them. So on an NPC1 you can rename Attack 1 to "Sword" and on NPC2 you can name it "Dagger".
- Show Units?: If haveing more than a cItem of the same type is important for the table you want, mark this. When checked, a new column will appear "Num", that registers the number of specific cItems you have. As we are preparing an Inventory, this options seems important, so check it.
- Has Activation?: if checked, two new columns will appear. One, the "Activation Button" column, this means that if a cItem is consumable or can be activated (later explained), it will show here. As an example for this, imagine you have a Healing Potion, that you have just dragged onto the Inventory. The Healing Potion has been set as a Consumable cItem, so a button appears on the activation button column, and when you press it, it rolls the HP recovered for example. The other column that is added to the table is the "Uses", so if a consumable cItem has limited number of uses, it will show here. In the example of the Healing Potion, if we set the cItem max uses as 1, it will show here. Let's check this one for our example.

That sounded complicated, but is easier than it looks! Your table property should look this way:

![Creating a Table II](docs/images/tuto22.png)

Now we have to add it to a Panel, so create a new Panel, let's say 1/2 width, 1 column, and drag the Table Property to it. 

![Adding Table to Panel](docs/images/tuto23.png)

Finally, add the Panel to our Stats Tab, and go to our Template Actor and Rebuild the Sheet. 

![Adding Table Panel to Tab](docs/images/tuto24.png)

Press F5, create a New Actor and assign our Template Actor sheet, and voila:

![Ckecking Table on Sheet](docs/images/tuto25.png)

Well, we can't see much. But the Header is there, and you can see "Weight", the main property we added to our Group! So it works. To confirm this, we need to add some cItems, so let's create a couple of cItems, a Torch and a Backpack. Remember, to create a cItem we only have to create a new Item and selecto the type, but the important thing is... don't forget to drag the group to it! In our case, we drag the Object group and set Weights of 2 for the Torch and let's say 1 for the Backpack.

![Adding cItems for table](docs/images/tuto26.png)

Now, let's drag these two cItems from the Items Directory onto the New Actor. And boom! Try to drag another Torch, and you will see that Num increases... Perfect, simply perfect. Well, we should have used a wider panel, probable 2/3 or 1, but still looks great:

![Adding cItems for table](docs/images/tuto27.png)

TRICK: you can set a table with only 1 cell if you use a unique group for the table definition! So if you want to create the Race field and have it populated with the race name every time you drag and drop a race cItem over it, this is your option (and also, select ONLY NAMES for the Item Names option).

![Adding Tables of 1 cell](docs/images/tuto28.png)

TRICK 2: if your group has a textarea property (you know, those huge areas that can get filled with text) an icon like this will be shown. So if you click it a Dialog will display with the entirety of the text. You can edit it in the Dialog if the textarea property is not constant in the group. This is useful to create PbtA games moves and list them.

![Textareas and tables](docs/images/tuto29.png)

TRICK 3: if you want a rollable button in a row, just create a label property, with the Label Format property set as Die. Then of course, set your roll with the Rollable checkbox options of the Property (explained in section 7), and voila:

![Rolls and Tables](docs/images/tuto30.png)

## 6.Modifiers (MODs)
Now, get ready for the difficult stuff, rules automation. Sandbox is based on the following mantra: character sheets are modified by cItems, and rule systems can be modelled by designing a cItems structure. So, every modification a cItem performs to an Actor is called MOD. Let's get to it.

![cItem MOD Execution Type](docs/images/tuto31.png)

Remember that MODs necromancy tab in the cItem window I talked about? Now is the time to open it. The first thing we see is the MOD Execution type selector. The Execution Type is the way we set the cItem to use MODs, and the selector allows you to choose between: Passive, Consumable, Activation.
- Passive: the MOD is always executed. Example for this: let's say our "Dwarf" cItem that we mentioned before has a MOD that adds the "Darkvision" cItem as we suggested. "Dwarf" will have an execution type of "Passive", because whenever it is on an Actor Darkvision should be added automatically.
- Consumable: the MOD is only executed when we click the activation button on a table, and after it's clicked the MOD stops executing. Example of this: a Healing Potion cItem. If we set it as Consumable, when we click the activation button it will add the HP we set it with, but that's it, it won't keep adding it indefinetly.
- Activation: the MOD is only executed when we check the activation checkbox on a table, and stays activated while it's unchecked. Example of this: a Chainmail Armor. If we set it as Activation, the cItem adds +4 to the Actor's AC as soon as we check the activation checkbox (meaning the Actor is wearing it).

Now, let's go through the options we have for the Execution Types:

![cItem MOD Execution Type Options](docs/images/tuto32.png)

- Self-destroy: the cItem will self delete from the Actor once executed. When would this be useful? I still have my doubts, but I will leave this just in case anyone needs it, although if a PASSIVE cItem needs to get destroyed after activation, then is not passive...
- Permanent: If checked, the MOD effects will stay even if the cItem or MODs have been deleted/deactivated. When would this be useful? Let's go back to the Healing Potion example. If you don't select the Permanent check, the HP the Actor would gain after activating it would dissapear as soon as we delete the Healing Potion from the inventory. If we check it, the gained HP would stay even if the Healing Potion is removed from the inventory.
- ICON: Is the icon that will be displayed on the Activation column of tables (see previous section);
- Uses: Max number of uses of the consumable. It is shown in a table if its Item Number property is activated. The GM can manually edit it on the table. If you set it as 0, then the max uses ar infinite.
- Rechargable: Every time the activation button is clicked for a Consumable cItem, the number of uses is reduced by 1. When it reaches 0, the cItem is deleted from the Actor. If you check rechargable, this won't happen. When is this useful? Well, imagine that your system has rechargable magical items, let's say rings or wands with a number of charges of spells. But once spent, you can still recharge them. This would serve for that.
- Roll Options: When the cItem is activated a roll is executed if this info is filled. Will be explained in the next section.

Wow, that was intense. Why did a do this? To give you all the options you need to build your favourite ttrpg system in Foundry, without coding. So you can build it in a lazy Sunday afternoon. But we haven't finished. Now comes the cool part, MODs.

Every cItem can have any number of MODs of different types (not Execution Types, that is only one type per cItem, we are talking now MOD Type). You can add MODs using this button:

![adding MOD to cItems](docs/images/tuto33.png)

The MOD menu has the following options:
- Description: If you need a short description to identify what the MOD does, put it here. By default it says "New Mod".
- MOD Type: There are 4 types of MOD: ADD, SET, ITEM, ROLL. They will be explained shortly.
- Conditional: Imagine you want a MOD executed only on specific values of specific attributes. This is your place. Introduce the conditional attribute name, the comparison (NONE or > or <), and the value it needs to have. When can this be used? Well, for example in D&D all classes get attribute increase options at level 4. This is a MOD with a level condition, effectively. So, if you were creating a D&D sheet with the "level" attribute, you would just configure it here and set the ">" comparison to 3. And the MOD would execute only if the level was 4 or higher.
- Specific row per each MOD Type: every Type has a row that we will look at in detail now.

Let's look at each MOD Type in detail:
- ADD: Will add a number to the attribute value of the Actor. An example of this would be the constitution bonus of Dwarves in D&D. So the cItem could perfectly be "Dwarf", with a group called "Race", and a MOD Execution Type of "PASSIVE". By the way, attributes increased by a MOD show up in a green colour:

![ADD MOD type](docs/images/tuto34.png)

- SET: Will set the value of an attribute to a number. You can also set the Maximum value of an attribute by using "nameofattribute.max". An example of this would be armor in D&D. Let's say we created the cItem Chainmail Armor with a group called Armor. This group could have a property called armorAC, so every Armor cItem could have its own attribute value. And when configuring the MOD, you could simply say that it sets the AC attribute value to the cItem's armorAC attribute value. How to do that? With a little roll notation, instead of value you would write #{armorCA}. I will explain this in the next section... I have said that a lot, haven't I?

![SET MOD type](docs/images/tuto35.png)

-ITEM: My personal favourite. It adds a number of cItems to the Actor. You only have to drag and drop the cItems you want to add with the cItem onto the ITEMS panel. You will see that there is an option called SELECT. If you leave that to 0, all cItems will be added to the  Actor. If not, the player will have to choose a number of cItems from the list. When to use this? Everywhere... For example, in D&D, players choose a barbarian path, or a bard college... this would be the way to do that. On another example from different games... this is the way you could have players choosing their playbook on a pbtA, or their initial movements. How do they choose? A white exclamation mark on a red circle will appear on their character sheets.

![ITEM MOD type](docs/images/tuto36.png)

-ROLL: Every roll can have one or more Roll IDs. A Roll ID is a word, a key (no spaces then), and you can define it within the roll expression or by using the roll options input field called Roll ID. With this MOD you modify every Roll with a specific Roll ID with a value. When to use this? For example, again D&D, you would have a cItem called Rage, with the group Trait, and within this you could add a ROLL MOD that would add the Rage Damage value to every roll with a Roll ID of "melee_attack" or whatever you want to ID the melee attacks rolls in your system. For example, on Savage world you could create a cItem called Wild Attack, with the group Combat Option, and as MOD a ROLL that would add +2 to rolls with the ID "fighting" and "damge" or whatever you want to call them. So before setting ROLL MODs make sure you have an idea of the roll IDs you need on your system. In general, before start MODding, have a think of the structure.

As MODs interact directly with the Actor and change it's attributes, you need to have an idea of the final attributes (created by Properties as we have seen before) before you create one. For example, if your cItem MOD increases the attribute "strength", it's not going to work unless that attribute has already been created by the character sheet (through a Property on a Template Actor, as explained before). Remember that a cItem is only displayed on a Table in a character sheet!

One last thing, you can use roll expressions when setting values of a Mod. What is that? Comping up next... But as an example:

![Roll Expressions and MODs](docs/images/tuto37.png)

## 7.Roll Expressions
Wow, you deserve a medal. You still haven't run away... So welcome to the final chapter of the Book of Secrets. This might affect your Sanity. By the way roll Sanity. Oops, sorry, I haven't taught yet how to define rolls MUAHAHAHAHAHA.

Ok, let's get to it. Rolls can be defined at Property menus (Details tab, checking the "Rollable" option) or cItem menus (Mod tab, but only for cItems that are not PASSIVE). These menus where you can define de roll are called Roll Options, and they look like this:

![Roll Options](docs/images/tuto38.png)

The fields mean the following:
- Roll Name: What title will the roll template display. For example "Strength check", or "Death Save", etc.
- Roll ID: this is the main roll ID, an identifier or Key that the roll will belong to. It doesnt have to be unique, so if your system has a lot of skills and this is a roll fo one of them, you just can use "skill" as roll ID.
- Roll Expression: the roll itself, like 1d6 or 1d20 + 5, etc.

There is a list of functions to use with roll expressions. Now you will hate me for this, but I am horrible with Regex, so these functions are ugly, very bad looking. Bear with me, if you help me we can improve them. You can also use them in MOD value definition fields. The functions are the following:
- ceil(): A classic, rounds to the highest number. Example: ceil(2.5) => will return 3 in the roll on chat
- floor(): It rounds to the lowest number. Example: ceil(2.5) => will return 2 in the roll on chat
- max(): returns the maximum roll of a simple dice roll, like 1d6, 2d6, 3d8, etc.
- @{character_attribute_name}: so, imagine that the Key of the Level Property is "lvl". You can reference it on the roll with @{lvl}. So if you need to roll 1d6 + level to the chat you just use: 1d6+@{lvl}
- #{citem_name_attribute}: if you are using a roll expression from a cItem you can reference one or more of its attributes with this. As an example, imagine a cItem has a "damage" property, and you want a roll expression to roll 1d6 + this attribute. So the roll expression would be 1d6+#{damage}. Remember @{} is for Actor attributes, #{} is for cItem attributes.

![Referring cItem attribute](docs/images/tuto39.png)

- %[expression,0:min return,value1:return_for_value1,valueN:return_for_valueN]: You know that in many ttrpgs you have a value and a modifier related to it. And most of the times the calculation of the modifier is not a simple arithmetic calculation, is more of a table search. For example, you could have a system that requires you to roll 1d20 for a number of traits, and from 1 to 10 the trait modifier would be +0, 11 to 12 would be +1, 13 to 16 would be +2, and 17+ would be +3. So I created this expression to deal with that, simply by using %[1d20,0:0,11:1,13:2,17:3]. Easy, and very useful.

![Referring cItem attribute](docs/images/tuto40.png)

- if[expression:compared_value,return_iftrue,return_iffalse]: very useful expression especially for text attributes. Let's say you have a system in which you want to check if the attribute called "ismagical" of a specific cItem is true, and in case it is you want to return 2 to the roll chat. So the expression you need is [#{ismagical}:true,2,0]
- --cItem_attribute_name--: This function returns the value of a cItem attribute if you pase the attribute's Key to it. Lets imagine we set Torch (the cItem created earlier as an example) as a CONSUMABLE MOD and fill the Roll Options fields. If we set its roll expression as "1d6 + --weight--" it will roll to chat 1d6 plus the value of its Weight attribute (remember we defined it as part of the Group object).
- __ Actor_attribute_name __: This function returns the value of an Actor attribute if you pase the attribute's Key to it. Imagine you have a list type Property of Key "selectedskill" on your character sheet, and this list has as options all the available skills in the system (i.e: climb, deception, swim, etc). You want to make this property rollable, and when clicked you want the sheet to roll 1d6+the value of the selected skill. You need then to reference the skills (which are attributes), so you can do this with "1d6 + __ @{selectedskill} __" . How does this work? When you select, let's say the "climb" option, this function will return __ climb __, that is equivalent to @{climb}. By the way, no spaces, I just included them to avoid bold formatting here...
- |Expression : This functions prevent Sandbox from parsing roll expressions, returning them as text. For example, lets say you just want to return to the chat "1d6", without rolling the 1d6, you just want a text saying "1d6". You then have to use |1d6 in your roll expressions.
- #{name}: Returns the name of the cItem you are rolling from.
- #{roll}: Returns the value of the latest roll executed on a cItem. How is this useful? Well, imagine you have a cItem that is a CONSUMABLE, and every time is activated it rolls 1d6. If you want that 1d6 result to be added to an attribute as part of an ADD MOD, you just need to use #{roll} in the MOD value input field.
- #{num}: returns the current number of units of the cItems that this actor has.
- #{target|target_attribute_key}: Returns the value of an attribute of the target actor on the map. Useful for calculating AC and such. Example: 1d20 + @{weapon_skill} &&0:FAILURE;#{target|ac}:YOU HIT!&&
- #{diff}: There is a DC box on the bottom of your active scene, to the right of the macro bar. DC stands for difficulty class. If your system/game requires the GM to set a difficulty, this is the place to write it down. Then, the rolls can reference this difficulty by using #{diff}.
- &&value_1:text_1;value_N;text_N&&: So imagine you want to return a sentence to the chat, along with your roll. You want to return "SUCESS" if the result of your roll is over 8, "FAILURE" if the result of the roll is under 7, and "PARTIAL SUCCESS" on every other result. This function allows you to return that sentence/word below the roll result. So you can do this with the following formula &&0:FAILURE;7:PARTIAL SUCCESS;9:SUCCESS&&

![Success and Difficulty rolls](docs/images/tuto41.png)

- ¬¬expresion, result1:value1,result2:value2¬¬: This function is an advanced successes calculator. Imagine you need to count the number of dice equsl to 5 or higher in a 4d6 roll. You use then ¬¬4d6, 0:0,5:1¬¬. This means that for every die equal or higher to 5 it will return 1. So for a roll of 3,4,5,6 it will return 2. But what if we want to add that every 6 should return 2 instead of 1? We just add it as an option to the formula like this: ¬¬4d6, 0:0,5:1,6:2¬¬ So for a roll of 3,4,5,6 it will return 3.
- ~Roll_ID~: adds a Roll ID to the roll. Remember that we have a MOD type called ROLL? And this one adds values to rolls of a specific Roll ID? So this function lets you add ROll IDs to rolls. As many as you like. So let's say we just defined a roll for an attack with Roll Name:"Attack", Roll ID: "attack", and Roll Expression: 1d20+@{strength}. However, we want more definition for it, and for that we want to incorporate some more Roll IDs, in case we need to modify the roll through a MOD. Let's say we want to add the Ids "melee_attack" and "slashing", then we would have to change the Roll Expression to 1d20+@{strength} ~melee_attack~ ~slashing~
- ~ADV~ or ~DIS~: fives advantage or disadvantage to the roll
- ~init~: sends the result of the roll to the initiative on the combat tracker.

![Rolling to initiative](docs/images/tuto42a.png)

- !(Roll Name;Roll Expression): If you want to have a roll separated from your roll expression, with a name, and displayed by its own, you use this formula. For example, imagine that for a system we are designing we need to roll 1d6 with every skill check, and this die is called the "Anger Die". You could set it up like this: 1d10 + !(Anger Die;1d6).

![Naming sub rolls](docs/images/tuto44.png)

- $<index;expression>: So roll parsing is not perfect, and until we find a way to do it more visually attractive there will be tons of problems. Expressions that contain brackets inside other expressions that also contain brackets will give you troubles. To avoid this, you can save pieces of your expression through this function. For example $<1;%[@{str},0:0,15:1]> will register the expresion after the semicolon as $1. A full example of this is: $<1;%[@{str},0:0,15:1]> 2d6+$1. This expression is equivalent to 2d6 + %[@{str},0:0,15:1]. Remember to change the number before the semicolon, as is the index and will let you identify subexpressions using $1,$2,$3, etc.

## 8.Folder structure best practices
If we want to share our creations and systems, we will have to standardise the way we store Sandbox's info. In the future, we could try to include a button to export to db or something like that, I don't know. But for know, let's stick to this structure. In the Actors Directory I normally create 2 folders, one called _CONFIG, and one called CAMPAIGN. In _CONFIG, and within separate folders, I store each Template Actor that the system needs (one for PCs, other for NPCs, other for shared menus like shared inventory, etc).

And on the Items Directory, I keep 2 main folders. One called _COMPENDIUM and the other called _TEMPLATE. Within _COMPENDIUM I create a _CONFIG folder, in Which I include Groups (stores group items),and Group Properties folders (stores properties used for groups).Within the _COMPENDIUM folder I also include separate folders for compendium items created, specific to the system, like Races, Classes, Objects, etc.

In the _TEMPLATE folder I create 3 folders: _TABS, _PANELS, _PROPERTIES. On some systems, it could be useful to create 2 folders inside _PROPERTIES, for _PC,_NPC, if both character sheets are too different.

![Folder Structure](docs/images/tuto43.png)

Well, that's all. It can feel like chaotic and a mess, but it works. I have been creating systems, playing, and streaming them in my channel for these past 3 months, and it works great. I will do my bust to update the tool and create English tutorials as frequently as possible. Thanks for your understanding and enjoy!!

## TODO LIST
- Check release notes

## FINAL THANKS
- To James, Mikel, Enrique, Viletus. You guys are the best, and we together will put our hobby in the place it deserves. 
- To Goblin Enmascarado: Thanks man, you rock, your Sandbox D&D compendium in Spanish is amazing!
- To Dr.Slump: Thanks for the ideas and the help! You learnt this chaos too fast!
- The Rol NL discord community: because your support has been instrumental to achieve the objective. Thanks for your help!!
- The Foundry discord community: for answering all my questions, I know they could sound strange XD