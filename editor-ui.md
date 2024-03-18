# Using the Editor

The UniUI editor is a pretty neat tool. You can create whole interfaces - visually!
To get started, you should probably [open it up](https://tizudev.vercel.app/uniui/editor).

For this guide, we're gonna be building a simple `Sculk Mode` interface. By the
end of this we're gonna have an interface that allows a user to toggle a Sculk
Sensor, Calibrated Sculk Sensor or Sculk Shrieker between these three. If the
calibrated sensor is selected, a new button will appear that allows the user
to configure what it should be calibrated to. There's also gonna be a delete
button - cuz why not?

Let's get building!

---

If you wanna check out the finished Editor project-

(- example fdb29bdb7b9a90c32fe8073cd3450349 -)

## Interface setup

Click on the `My Awesome Interface` input field and type a name for the UI, like
`Sculk Mode`. Then, press create. The main editor interface is gonna open up.

Our UI only takes up a single row, so let's change that. On the right, look for
the `Rows` field, then change it to `1`. Watch the fancy animation, then.. yea,
that's it.

## Adding tiles

We obviously need the actual tiles. On the left, click `Create new tile`. Let's
build the delete button first - it should be the easiest. Click on the `Button`
tile - that blue square. We should be prompted for a name and other stuff, so
let's go over that.

- Let's name the tile first, as it's crucial for our workspace to be organized.
  What about `Delete`? Great!
- We don't want the delete button to be disabled - that'd be pretty useless.
- For the accent color, you may pick any. However, you may just click the red
  one on the right if you don't feel like picking your own color.
- This is the tricky part - you gotta draw. Draw a trash can as the icon.
  However, we made a fancy trash can template for you, if you wanna use that.
- For the icon style, just keep the default. Feel free to try the others out,
  but I doubt you'll like them. One of them is meant for the gray color preset,
  the other.. I don't know - it's just there.
- Let's keep our button at 1x1 slots. If we increase it in size now, the other
  button won't fit!

Great job! Now click the button preview at the bottom and it'll create the tile.
*Your tile got saved just now! It's gonna stay there, even if you refresh.*

Click the newly created tile, then click on a slot. In my case I want the delete
button to be in the last slot, so I'll just click that, but anything goes! If
everything went well you should see the button there. Great!

> You can remove a tile from a slot by placing a different tile or right clicking.
> If the tile is larger than 1x1 sq, you have to right-click the anchor slot.

Yea, adding buttons is as simple as that. Don't believe me? Click the `Preview`
button in the bottom-right corner. Wait for it to render, and you should see
your texture *with the button*. Yup!

Now, create three more buttons, for the three modes. I decided to call mine
`Mode: Sensor`, `Mode: Calibrated` and `Mode: Shrieker` respectively. Use the
icon to display what block they are, then change the accent to the gray one and
use a size of 2w x 1h. I also changed the icon rendering to dark, as it looks
nicer. Repeat this for the other two modes. We won't place them (for now).

## Managing Tiles

Oh yea - I forgot! The `More` button! Let's use the `Delete` button as a template.
Right click it in the toolbox, then select `Clone this tile`. Right click the new
tile, then select `Modify this component`. Change the accent to blue, rename it
to `More`, change the icon and disable it. Click on the preview to save, then
place it next to the `Delete` button.

Now, clone the three mode buttons. Edit them to be disabled. You might prefer
changing the icon style to light, although that's up to you. Great!

Let's place the *disabled* buttons down. I placed them on the left, ordered
`Sensor`, then `Calibrated`, and finally `Shrieker`. Neat.

## Components (layers / states)

Now, let's get to adding states - layers - *components*! Components are

> The layers of your interface. Should've been called layers, but the original
> idea was that you could toggle buttons (so components!?) using these layers,
> so I called the layers components.

On the right, click on the wrench icon next to the `Component to edit`. Give
your components a name, like `sensor`, `calibrated` and `shrieker`.
You might've noticed that your tiles moved to the background. That is normal,
do not fear - you can revert this by switching back to the default component.

Switch to the `sensor` component (by selecting it in the dropdown). Then, click
on the *enabled* `Mode: Sensor` tile in the toolbox that we created earlier.
Click on the *disabled* sensor tile on the interface - the one that's below
the blue "here's nothing!" tiles. Repeat this for the other two components.
Neat - that's it!

The `calibrated` component is special - forgor? It should enable the `More`
button. Clone the `More` button, uncheck `Disable` on the clone, then place
it above the disabled `More` button. Make sure you're editing the right
component. Aha!

---

**This guide won't cover the `More` button!** You can easily create an interaction
(continue reading this guide) that opens another interface, and I will cover how
to do that, but you're on your own creating the second interface. However, it's
as simple as creating a new UniUI editor project. Yup!

## Interactions

Let's add interactivity to our UI. On the 
right, select `Edit interactions`. Now, click on the delete button tile. Give it a
name, like `Remove block`. Submit this, then do the same thing for the other buttons.
Make sure to set interaction zones for both sides of a button if it's two wide - this
enforces you to name them the same thing. If everything went well, they should both be
highlighted with the same color. Cool!

> I named mine `Remove block`, `Configure block`, `Switch to Sculk Sensor`,
> `Switch to Calibrated Sculk Sensor`, and `Switch to Sculk Shrieker`, by the way.

You basically just registered the slots that UniUI should treat as clickable, as well
as their tooltip label. Yea, that's it.

## Exporting

Let's preview what we just created. Click the `Preview` button! This might
take a sec, as it has to render all four (`Default` + the three custom ones)
components. You should see all your layers in the bottom-left corner. Hover
over one of them, then click the arrow buttons to reorder the list. Using this,
move one of the components above the `Default` one. There ya go! Easy as that.

If you're happy with how this turned out, feel free to export it into your game.
This is fully automatic. **However, this requires your pack to have UniUI
installed. See [this](https://tizudev.vercel.app/uniui/docs/getting-started).**

Got it? Neat! Run `npx uniui-kjs@latest generate`, then click `Export` from within the
editor. Wait for the editor to render everything, then continue in the CLI. If you
need help, click the `Next steps` button on the `Exported!` screen.
