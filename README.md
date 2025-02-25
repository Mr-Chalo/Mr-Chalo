# Typing Effect Example

To see the typing effect in action, view this README file in a browser that supports HTML and JavaScript rendering.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Typing Effect</title>
    <style>
        .typing-effect {
            font-family: monospace;
            white-space: nowrap;
            overflow: hidden;
            border-right: 0.15em solid black;
            animation: blink-caret 0.75s step-end infinite;
        }

        @keyframes blink-caret {
            from, to { border-color: transparent; }
            50% { border-color: black; }
        }
    </style>
</head>
<body>
    <div>I am a <span class="typing-effect" id="typing-text"></span></div>

    <script>
        document.addEventListener("DOMContentLoaded", function() {
            const words = ["Student", "web cloner", "programmer"];
            let wordIndex = 0;
            const delay = 1500; // delay in milliseconds

            function typeWord() {
                const word = words[wordIndex];
                let index = 0;
                const typingTextElement = document.getElementById("typing-text");
                typingTextElement.innerHTML = "";

                function type() {
                    if (index < word.length) {
                        typingTextElement.innerHTML += word.charAt(index);
                        index++;
                        setTimeout(type, 100);
                    } else {
                        setTimeout(() => {
                            wordIndex = (wordIndex + 1) % words.length;
                            typeWord();
                        }, delay);
                    }
                }

                type();
            }

            typeWord();
        });
    </script>
</body>
</html>