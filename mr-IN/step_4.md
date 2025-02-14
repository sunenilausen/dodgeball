## गुरुत्वाकर्षण आणि उडी मारणे

आता आपण आपले पात्र अधिक वास्तविकपणे कसे हलेल ते पाहणार आहोत: आपण आपल्या गेममध्ये गुरुत्व जोडू आणि त्या पात्राला उडी मारण्याची क्षमता देणार आहोत.

--- task ---

खेळात आपल्या पात्राची हालचाल अशी करा जेणेकरुन ते फलाटा बाहेर पडेल. तुम्हाला लक्षात आले का ते रिकाम्या जागेत चालू शकत आहे?

![screenshot](images/dodge-no-gravity.png)

--- /task ---

--- task ---

हे सुधारित करण्यासाठी आपल्या गेममध्ये गुरुत्वाकर्षण जोडा. हे करण्यासाठी `gravity`{:class="block3variables"} नावाचे नवीन व्हेरिएबल तयार करा.

[[[generic-scratch3-add-variable]]]

आवश्यकता वाटल्यास तुम्ही हे व्हेरिएबल लपवू शकता.

![screenshot](images/dodge-gravity-annotated.png)

--- /task ---

--- task ---

हे नवीन कोड ब्लॉक जोडा जे `gravity` ला ऋण अकड्याने प्रस्थापित करेल आणि `gravity` चा उपयोग करून तुमच्या पात्राची y-coordinate सतत बदलत राहील:

![pico walking sprite](images/pico_walking_sprite.png)

```blocks3
    when flag clicked
    set [gravity v] to [-4]
    forever
        change y by (gravity)
    end
```

--- /task ---

--- task ---

ध्वजावर क्लिक करा आणि नंतर आपल्या पात्राला स्टेजच्या शीर्षस्थानी ठेवा. काय होते? आपल्या अपेक्षेनुसार गुरुत्व कार्य करत आहे का?

![screenshot](images/dodge-gravity-drag.png)

--- /task ---

--- task ---

गुरुत्वाकर्षणामुळे आपले पात्र फलाटाच्या आरपार नको जायला! तुमच्या कोडमध्ये एक `if`{:class="block3control"} ब्लॉक जोडा जेणेकरून तुम्ही गुरुत्वाकर्षणाला फक्त पात्र हवेत असताना चालू ठेऊ शकाल. आपल्या गुरुत्वाकर्षणाचा कोड असा दिसला पाहिजे:

![pico walking sprite](images/pico_walking_sprite.png)

```blocks3
    when flag clicked
    set [gravity v] to [-4]
    forever
        if < not < <touching color [#0000FF]?> or <touching color [#FF69B4]?> > > then
            change y by (gravity)
        end
    end
```

--- /task ---

--- task ---

गुरुत्वाकर्षण आता योग्य प्रकारे कार्य करते की नाही हे पाहण्यासाठी पुन्हा खेळाची चाचणी घ्या. तुमचे पात्र जेव्हा शिडीला किंवा फलाटाला स्पर्श करतो तेव्हा ते खाली पडायचे थांबते का? आपण पात्राला प्लॅटफॉर्मच्या काठावरुन खाली पडून खालच्या पातळीवर जायला भाग पडू शकता?

![screenshot](images/dodge-gravity-test.png)

--- /task ---

--- task ---

आता जेव्हा खेळाडू <kbd>स्पेसबार</kbd> दाबेल तेव्हा पात्राने उडी मारावी ह्याकरता कोड जोडा. असे करण्याचा एक अतिशय सोपा मार्ग म्हणजे आपल्या पात्राला काही वेळा वर आणणे:

![pico walking sprite](images/pico_walking_sprite.png)

```blocks3
    when [space v] key pressed
    repeat (10)
        change y by (4)
    end
```

कारण गुरुत्व तुमच्या पात्राला सतत 4 पिक्सेल ने खाली ओढत आहे, त्यामुळेच तुम्हाला तुमच्या `change y by (4)`{:class="block3motion"} कोड ब्लॉकमध्ये `4` पेक्षा जास्त मोठा आकडा निवडावा लागेल. जोपर्यंत पात्राची उडी मनासारखी होत नाही उंचीचे आकडे बदला.

--- /task ---

--- task ---

आपला कोड तपासून पहा. लक्षात घ्या की उडी मारण्याची हालचालीत गचके येऊ शकतात. उडी मारणे सोपे करण्यासाठी, तुम्हाला तुमच्या पात्राला कमी कमी प्रमाणात हलवावे लागेल, जोपर्यंत ते अजून उंच होणे थांबेल.

--- /task ---

--- task ---

हे करण्यासाठी `jump height`{:class="block3variables"} नावाचे नवीन व्हेरिएबल तयार करा. परत एकदा, आवश्यकता वाटल्यास तुम्ही हे व्हेरिएबल लपवू शकता.

--- /task ---

--- task ---

आपण आपल्या पात्राला जोडलेला उडीचा कोड पुसा आणि त्याऐवजी हा कोड जोडा:

![pico walking sprite](images/pico_walking_sprite.png)

```blocks3
    when [space v] key pressed
    set [jump height v] to [8]
    repeat until < (jump height) = [0] >
        change y by (jump height)
        change [jump height v] by (-0.5)
    end
```

हा कोड आपल्या पात्राला 8 पिक्सेल, नंतर 7.5 पिक्सेल, नंतर 7 पिक्सेल आणि इतक्या वर नेतो जोपर्यंत पात्राला अजून उंच होता येणार नाही तोवर. यामुळे उडी मारणे अधिक नितळ होते.

--- /task ---

--- task ---

`jump height`{:class="block3variables"} व्हेरियाबल ची व्हॅल्यू अशी बदला की ती `repeat`{:class="block3control"} चालू होण्याच्या आत सेट होईल. मग आपल्या खेळाची चाचणी घ्या.

जोपर्यंत पात्राची उडी मनासारखी होत नाही तोपर्यंत ह्या दोन पायऱ्या पुन्हा करा.

--- /task ---