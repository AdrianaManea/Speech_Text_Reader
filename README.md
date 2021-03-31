## Speech Text Reader

A text to speech app for non-verbal people.
This project uses the Web Speech API - https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesis
Pre-made buttons and custom text speech.
Stop speaking button

## Project Specifications

- Create responsive UI (CSS Grid) with picture buttons
- Speaks the text when button clicked
- Drop down custom text to speech
- Read text btn typed in
- Clear text btn typed in
- Stop speaking btn
- Change voices and accents

## JS - How it's made

- Everything, except the boxes, is straight HTML
- In the <main></main> we're putting/outputting each box from the array called data

- Create array = data
- An array of objects that has 2 things: img and text
- Loop through data with createBox(item)
  - forEach needs to take in 'item'
  - build the boxes in our UI
    - const box = create div element
    - destructuring - pull the image and text from the item
      - const { image, txt } = item;
      - item is an object with image and text as it's two properties and we're pulling them out so then we can use image and text further on instead of item.image and item.text
    - add .box class to out box div
    - box add innerHTML
      - create elements for text and image
    - appendChild(box) to main forEach box, forEach iteration
- Add the toggle functionality/text box
  - .text-box.show - in CSS we styled the class of .show to transform: translate(-50%, 0); to bring it down to it's original spot when click 'Toggle Text Box' btn
- Add the close btn functionality
- Fill the voices
  - Store voices
    - let voices = [];
    - create function getVoices()
      - set voices variable to SpeechSynthesis and .getVoices() method
      - loop through 'voices'
        - forEach voice we run a function
          - run an option
            - create option element
            - option.value = voice.name;
            - option.innerHTML = `${voice.name} ${voice.lang}`;
          - append option to voiceSelect
  - Event Listener for when the voices change
    - speechSynthesis.addEventListener('voiceschanged', getVoices);
  - call getVoices() at the end
- Create the functionality to speak
  - In the createBox(item){} add Speak Event Listener
    - so each box when we click it it's going to run a function
    - call setTextMessage(text); which sets the message we want to speak which is going to be the text from that iteration/(item)
    - call speakText();
    - add an active effect
      - add the active class on box with a setTimeout of 800ms to give us the effect we set for it in CSS
- Init const message = new SpeechSynthesisUtterance();
- Create setTextMessage(text)
- Create speakText()
- Change voice - event listener 'change', setVoice
  - Create setVoice(e)
- Read text btn
  - event listener 'click'
  - setTextMessage(textarea.value);
  - speakText(); - will speak whatever the 'message' is, which is set in setTextMessage(test){message.text = text;}
- Clear text btn
- Stop speaking btn
