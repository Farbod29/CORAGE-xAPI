## CONTENT

- [CONTENT](#content)
- [Learning Locker Receipts and Statements](#learning-locker-receipts-and-statements)
- [Setup Learning Locker](#setup-learning-locker)
- [VLC Statements](#vlc-statements)
  - [Actor](#actor)
    - [Actor-Example:](#actor-example)
  - [Verb](#verb)
    - [Verb-Example:](#verb-example)
    - [Standardize the verbs and URI](#standardize-the-verbs-and-uri)
      - [Vocabulary Development and Standards](#vocabulary-development-and-standards)
        - [Actor/Verb URI:](#actorverb-uri)
        - [Activity_URI for objects](#activity_uri-for-objects)
  - [Object](#object)
  - [Timestamp](#timestamp)
    - [Timestamp-Example:](#timestamp-example)
  - [Context](#context)
- [VLC Verbs](#vlc-verbs)
  - [VLC Verb Answered](#vlc-verb-answered)
  - [VLC Verb selected-an-image](#vlc-verb-selected-an-image)
  - [VLC Verb text-entered (Wit-AI chatbot)](#vlc-verb-text-entered-wit-ai-chatbot)
  - [VLC Verb selected-button (recommendationSection)](#vlc-verb-selected-button-recommendationsection)
  - [VLC Verb selected-button (collaborationSection)](#vlc-verb-selected-button-collaborationsection)
  - [VLC Verb selected-button (ChatbotSection)](#vlc-verb-selected-button-chatbotsection)
  - [VLC Login statement template](#vlc-login-statement-template)
    - [Purpose](#purpose)
    - [Actor](#actor-1)
    - [Example:](#example)
      - [VLC Verb-login](#vlc-verb-login)
      - [VLC Verb logged-out](#vlc-verb-logged-out)
- [PixelFed Statements](#pixelfed-statements)
- [PixelFed - Verbs](#pixelfed---verbs)
  - [PixelFed Verb login](#pixelfed-verb-login)
  - [PixelFed Verb Image liked](#pixelfed-verb-image-liked)
  - [PixelFed Verb Image commented](#pixelfed-verb-image-commented)
  - [References](#references)
-

## Learning Locker Receipts and Statements

This documentation describes the **Receipts** and **Statements** format for our **xAPI** communication of records between different modules in companion system and simulated social media environment pixelFed.

![Screenshot 2021-07-25 at 01 15 14](https://user-images.githubusercontent.com/17232450/126883090-5c055e49-ca16-4c4c-ae69-202e1c238275.png)

We record and organize the user interaction with **V**irtual **L**earning **C**ompanion (**VLC**) and **PixelFed** area with **xAPI** standard format.
In conjunction with the PixelFed, VLC is a Chrome extension Plugin that can detect the user interaction with PixelFed artifacts. Each interaction be recorded in **L**earning **R**ecord **S**tore (**LRS**).
For the COURAGE companion project, Learning Locker is suggested for **LRS**.

![Screenshot 2021-07-25 at 01 16 33](https://user-images.githubusercontent.com/17232450/126883098-69a88b51-ed00-4d18-8a7e-24163d6ede76.png)

## Setup Learning Locker

Here in this link, you can find the Ubuntu16 server version (.ova) image, which we LL V7 was installed. As we know, server versions are lighter and compressed in comparison to the previous image Ubuntu16 Desktop LLv7.

[RIAS SERVER ](https://cloud.innowise.de/index.php/f/126501)

Current active LL is provided by CNR university:

https://analytics.pa.itd.cnr.it/login
Storage : ClosedEnvironmentAndCompanion

http://git.rias-institute.eu/fa/learing-locker-documentations/wikis/xAPI-Statements-for-the-COMPANION-and-PixelFed

## VLC Statements

The following templates define the structure and terms to record the user with experience the **V**irtual **L**earning **C**ompanion **VLC** as a chatbot inside chrome extension and its artifact, plus the user interaction with controlled social media environment **PixelFed** through **VLC** extension.
Natural language example of a typical Statement: "The user, who has the _*username*_ _mailto:usr838fh3@courage.eu_, has selected the image, which has the _id_ "http://couragepixelfed.eu/activities/2334" from the pixelFed and interacts with metadata, chatbot, etc. artifact in the chrome extension environment.

At the most superficial level, xAPI statement structure can be expressed in the form of **“actor verb object”**. An example of this sort of statement is “user answered ‘_Is that Fake or Not_?' question” . In the technical introduction, we see the JSON (Javascript object format) of this statement as follows:

### Actor

In the VLC and PixelFed, the actor entity identifies the individual that interacts with the artifact in both environments like chat with the chatbot, like and comment on posts, select image or metadata around it, etc. In the below example, the actor (VLC- Pixelfed User) started a conversation with the chatbot and answered the first question of the companion.

#### Actor-Example:

```Javascript
{
     "actor": {
        "mbox": "mailto:usr838fh3@courage.eu",
        "name": "usr838fh3"
    }
}
```

### Verb

**xAPI** is designed to track experiences that, by their nature, are time-based. Consequently, verbs are past tense because a statement has to be recorded (note past tense) for the experience. No matter how soon after a recorded experience is reported on, that portion of the experience must already be in the past.

#### Verb-Example:

The Verb **answered** Indicates that the actor has answered to the chatbot for an image to categorize it.

```javascript
}
   "verb": {
      "id": "http://adlnet.gov/expapi/verbs/answered",
      "display": {
        "en-US": "answered"
      }
    }
}
```

#### Standardize the verbs and URI

Each verb has its own description, which is accessible from a unique URI. with the specified domain. The domain is from the organization that responsible for xAPI Statements standardization like TinCan under the domain like below:

"http://id.tincanapi.com/activitytype/source"

##### Vocabulary Development and Standards

In the xAPI specification, there is no requirement to enforce a universal data model to agree on every type of learning activity that can be recorded. Instead, Activity Providers are free to publish different statements about the same activity using their profiles and vocabulary. This freedom provides great flexibility and resilience, but at the same time, can introduce disorderly practices (adlnet org)[1].

Here are our references for our statement and their URIs as and google sheet tables.

###### Actor/Verb URI:

https://docs.google.com/spreadsheets/d/1Jq7ROhj4bJOcYY8KrvXUPYs9lXPg25apXZBM2T6vAdQ/edit?usp=sharing

###### Activity_URI for objects

https://docs.google.com/spreadsheets/d/1hcoQ9ugI0BkbZ-lPPqSQphwBUlsLGXuJyAL449Zz844/edit?usp=sharing

### Object

Activity, Agent, or another Statement that is the Object of the Statement.

| Property                     | Description                                                                          | Value information |
| ---------------------------- | ------------------------------------------------------------------------------------ | ----------------- |
| object.objectType            | The value in must be "Activity".                                                     | String            |
| object.id                    | A unique identifier for the labeled image                                            | IRI               |
| object.definition.extensions | Information about the labeled image consistes of the id, the experince and the index | object            |

```javascript
  "object": {
    "id": "http://couragecompanion.eu/activities/Image143fg-COVID19-5G",
    "definition": {
      "name": { "en-US": "Image143fg-COVID19-5G" }
    }
  }
```

### Timestamp

An ISO 8601 format timestamp corresponds to the time when the labeling has occurred.
**Note:** when we do not indicate the Timestamp, the LL will automatically add a new Timestamp at the time of storing the xAPI statement.

#### Timestamp-Example:

```javascript
{
  "timestamp": "2021-01-27T22:02:48.375Z",
}
```

Our strategy is to add VLC and pixelFed-timestamp in the server-side of each module and add them at the end of the JSON file of each xAPI statement in the context field, so then we do not assign "timestamp" separately. As mentioned above, LL will automatically add a timestamp when receiving each statement to the end of the JSON of the xAPI. This helps us monitor each statement time for each module (VLC or PixelFed) and check if they are synchronous.

![Screenshot 2021-07-25 at 02 11 32](https://user-images.githubusercontent.com/17232450/126883754-075b5a16-f690-4e20-91d3-a260f4ef9911.png)

### Context

Describes the session in which the actor is, working environments server-side timestamps, and more information:

```javascript


   "context": {
         "extensions": {
                "http://nextsoftwaresolutions.com/xapi/extensions/user-info": {
                    "image-id": "http://couragepixelfed.eu/activities/2334",
                    "chat-Id" : "FakeOrNotQuestion",
                     "id": "http://couragepixelfed.eu/artifact/chat/FakeOrNotQuestion",
                    "environment":"VLC",
                    "vlc-time" : "162312432545",
                    "experienceID" : "5OCTOBER2021HRW"
          }
      }
    }
```

## VLC Verbs

The statements that are created by VLC.

### VLC Verb Answered

Describes the session in which the user answers the chatbot

```javascript
let xAPIStatement = {
  actor: {
    mbox: "mailto:usr838fh3@courage.eu",
    name: "usr838fh3",
    objectType: "Agent",
  },

  verb: {
    id: "http://adlnet.gov/expapi/verbs/answered",
    display: {
      "en-US": "answered",
    },
  },
  object: {
    definition: {
      name: {
        "en-US": "FakeOrNotQuestion",
        id: "http://adlnet.gov/expapi/activities/question",
        value: "yes",
        "expert-value": "yes",
      },
    },
    id: "http://couragecompanion.eu/artifact/chat/FakeOrNotQuestion",
  },
  context: {
    extensions: {
      "http://couragecompanion.eu/xapi/extensions/artifactinfo": {
        "image-id": "http://couragepixelfed.eu/activities/2334",
        "chat-Id": "FakeOrNotQuestion",
        id: "http://couragepixelfed.eu/artifact/chat/FakeOrNotQuestion",
        environment: "VLC",
        "vlc-time": "162312432545",
        experienceID: "5OCTOBER2021HRW",
      },
    },
  },
};
```

Same statement in the postman should be in open and closed **braket {}** like

```javascript
{
    "actor": {
        "mbox": "mailto:usr838fh3@COURAGE.eu",
        "name": "usr838fh3",
        "objectType": "Agent"
    },
    "verb": {
        "id": "http://adlnet.gov/expapi/verbs/answered",
        "display": {
        "en-US": "answered"
        }
    },
    "object": {
        "definition": {
        "name": {
            "en-US": "FakeOrNotQuestion",
            "id":"http://adlnet.gov/expapi/activities/question",
            "value" : "yes",
            "expert-value" : "yes"
             }
         },
    "id": "http://couragepixelfed.eu/artifact/chat/FakeOrNotQuestion"
    },
    "context": {
         "extensions": {
                "http://nextsoftwaresolutions.com/xapi/extensions/user-info": {
                    "image-id": "http://couragepixelfed.eu/activities/2334",
                    "chat-Id" : "FakeOrNotQuestion",
                     "id": "http://couragepixelfed.eu/artifact/chat/FakeOrNotQuestion",
                    "environment":"VLC",
                    "vlc-time" : "162312432545",
                    "experienceID" : "5OCTOBER2021HRW"
          }
      }
    }
}
```

for the other verbs we take the verb with the chatbot from the conversion id of the chatbot dynamically :

```javascript
let xAPIStatement = {
    actor: {
      mbox: `mailto:${data.companionUserToken}`,
      name: "usr838fh3",
      objectType: "Agent",
    },
    verb: {
      id: `http://xapi.vocab.pub/describe/?url=https://w3id.org/xapi/dod-isd/verbs/${data.conversationID}`,
      display: {
        `en-US": "${}`,
      },
    },
    object: {
      definition: {
        name: {
          "en-US": "${data.conversationID}",
          id: `http://adlnet.gov/expapi/activities/question`,
          value: `${data.value}`,
          expertValue: "${data.value}",
        },
      },
      id: "http://couragecompanion.eu/artifact/chat/"${data.conversationID}",
    },
    context: {
      extensions: {
        "http://couragecompanion.eu/xapi/extensions/artifactinfo": {
          "image-id": "http://couragepixelfed.eu/activities/2334",
          "chat-Id": "FakeOrNotQuestion",
          id: "http://couragepixelfed.eu/artifact/chat/"${data.conversationID}",
          environment: "VLC",
          "vlc-time": new Date().toISOString(),
          experienceID: ""${data.experienceID}"",
        },
      },
    },
  };

```

### VLC Verb selected-an-image

```javascript
{
    "actor": {
        "mbox": "mailto:usr838fh3@COURAGE.eu",
        "name": "usr838fh3"
    },
    "verb": {
        "id": "http://couragecompanion.eu/expapi/verbs/selected-an-image",
        "display": {
        "en-US": "selected-an-image"
        }
    },

      "object": {
        "definition": {
        "name": {
            "en-US": "FakeOrNotQuestion",
            "id":"http://couragepixelfed.eu/artifact/chat/FakeOrNotQuestion",
            "expert-text" : "the image is fake and the caption follows to proof fake image",
            "value" : "Yes"
             }
         },
    "id": "http://couragepixelfed.eu/artifact/chat/FakeOrNotQuestion"
    },
    "context": {
         "extensions": {
                "http://couragecompanion.eu/expapi/context-info": {
                    "image-id": "http://couragepixelfed.eu/artifact/image/2334",
                    "environment":"VLC",
                    "vlc-time" : "1624556432999",
                    "experienceID" : "5OCTOBER2021HRW"
          }
      }
    }
}
```

### VLC Verb text-entered (Wit-AI chatbot)

When the user in the chatbot writes a comment, asks a question, or replies as free text, then the chatbot will detect the user's intent and reply to the message. This is the user input statement template:

```javascript
{
    "actor": {
        "mbox": "mailto:usr838fh3@COURAGE.eu",
        "name": "usr838fh3"
    },
    "verb": {
        "id": "http://couragecompanion.eu/expapi/verbs/text-entered",
        "display": {
        "en-US": "text-entered"
        }
    },
      "object": {
        "definition": {
        "name": {
            "en-US": "WitAIChatbot",
            "id":"http://couragepixelfed.eu/artifact/chat/WitAIChatbot",
            "expert-text" : "the user describe his opinion about the privous topic in the free input text formant acd acording to the suggestions",
            "value" : "what is the answer for image related to the 5G?"
             }
         },
    "id": "http://couragepixelfed.eu/artifact/chat/WitAIChatbot"
    },
    "context": {
         "extensions": {
                "http://couragecompanion.eu/expapi/context-info": {
                    "image-id": "http://couragepixelfed.eu/artifact/image/2334",
                    "environment":"VLC",
                    "vlc-time" : "1624556432999",
                    "experienceID" : "5OCTOBER2021HRW"
          }
      }
    }
}

```

### VLC Verb selected-button (recommendationSection)

```javascript
{
    "actor": {
        "mbox": "mailto:usr838fh3@COURAGE.eu",
        "name": "usr838fh3"
    },
    "verb": {
        "id": "http://couragecompanion.eu/expapi/verbs/selected-button",
        "display": {
        "en-US": "selected-button"
        }
    },
      "object": {
        "definition": {
        "name": {
            "en-US": "recommendationSection",
            "id":"http://couragecompanion.eu/artifact/recommendationSection"
             }
         },
    "id": "http://couragecompanion.eu/artifact/recommendationSection"
    },
    "context": {
         "extensions": {
                "http://couragecompanion.eu/expapi/context-info": {
                    "image-id": "http://couragepixelfed.eu/artifact/image/2334",
                    "environment":"VLC",
                    "vlc-time" : "1624556432999",
                    "experienceID" : "5OCTOBER2021HRW"
          }
      }
    }
}
```

### VLC Verb selected-button (collaborationSection)

```javascript
{
    "actor": {
        "mbox": "mailto:usr838fh3@COURAGE.eu",
        "name": "usr838fh3"
    },
    "verb": {
        "id": "http://couragecompanion.eu/expapi/verbs/selected-button",
        "display": {
        "en-US": "selected-button"
        }
    },
      "object": {
        "definition": {
        "name": {
            "en-US": "collaborationSection",
            "id":"http://couragecompanion.eu/artifact/collaborationSection"
             }
         },
    "id": "http://couragecompanion.eu/artifact/recommendationSection"
    },
    "context": {
         "extensions": {
                "http://couragecompanion.eu/expapi/context-info": {
                    "image-id": "http://couragepixelfed.eu/artifact/image/2334",
                    "environment":"VLC",
                    "vlc-time" : "1624556432999",
                    "experienceID" : "5OCTOBER2021HRW"
          }
      }
    }
}
```

### VLC Verb selected-button (ChatbotSection)

```javascript
{
    "actor": {
        "mbox": "mailto:usr838fh3@COURAGE.eu",
        "name": "usr838fh3"
    },
    "verb": {
        "id": "http://couragecompanion.eu/expapi/verbs/selected-button",
        "display": {
        "en-US": "selected-button"
        }
    },
      "object": {
        "definition": {
        "name": {
            "en-US": "ChatbotSection",
            "id":"http://couragecompanion.eu/artifact/ChatbotSection"
             }
         },
    "id": "http://couragecompanion.eu/artifact/recommendationSection"
    },
    "context": {
         "extensions": {
                "http://couragecompanion.eu/expapi/context-info": {
                    "image-id": "http://couragepixelfed.eu/artifact/image/2334",
                    "environment":"VLC",
                    "vlc-time" : "1624556432999",
                    "experienceID" : "5OCTOBER2021HRW"
          }
      }
    }
}
```

---

### VLC Login statement template

#### Purpose

This template defines the structure and terms to record the experience of logging into the VLC companion.

Natural language example of a typical Statement: "The user, who has the _username_ **hrwcZSbk6** has logged into the companion website."

#### Actor

The actor entity identifies the individual that has logged into the companion website..

#### Example:

```Javascript
{
    "actor": {
      "objectType": "Agent",
      "account": {
        "name": "hrwcZSbk6",
        "homePage": "http://companion.eu"
      },
      "name": "hrwcZSbk6"
    }
}
```

##### VLC Verb-login

The Verb **login** Indicates that the actor has logged into the companion website.

```javascript
}
   "verb": {
      "id": "https://w3id.org/xapi/adl/verbs/logged-in",
      "display": {
        "en-US": "login"
      }
    }
}
```

the whole API body :

```javascript
{
    "actor": {
        "mbox": "mailto:usr838fh3@COURAGE.eu",
        "name": "usr838fh3"
    },
    "verb": {
        "id": "https://w3id.org/xapi/adl/verbs/logged-in",
        "display": {
        "en-US": "logged-in"
        }
    },
    "object": {
    "id": "VLC-extension"
    },
    "context": {
         "extensions": {
                "http://couragecompanion.eu/expapi/context-info": {
                    "image-id": "http://closed-environment.eu/artifact/image/2334",
                    "environment":"VLC",
                    "vlc-time" : "1624556432999",
                    "experienceID" : "5OCTOBER2021HRW"
          }
      }
    }
}
```

##### VLC Verb logged-out

```javascript
}
   "verb": {
      "id": "https://w3id.org/xapi/adl/verbs/logged-out",
      "display": {
        "en-US": "https://w3id.org/xapi/adl/verbs/logged-out"
      }
    }
}

```

---

## PixelFed Statements

The following statements templates define the structure and terms to record the user's experience with a controlled social media environment (PixelFed) **independent** with the VLC extension.

## PixelFed - Verbs

The statements that are created by PixelFed.

### PixelFed Verb login

Here in the context, the environment is pixelFed and the pixelFed-time is logged is the pixelFed server-side.

```javascript
{
    "actor": {
        "mbox": "mailto:usr838fh3@COURAGE.eu",
        "name": "usr838fh3"
    },
    "verb": {
        "id": "https://w3id.org/xapi/adl/verbs/logged-in",
        "display": {
        "en-US": "logged-in"
        }
    },
    "object": {
    "id": "closed-environment-pixelFed"
    },
    "context": {
         "extensions": {
                "http://couragecompanion.eu/expapi/context-info": {
                    "environment":"pixelFed",
                    "pixelFed-time" : "1624556432999",
                    "experienceID" : "5OCTOBER2021HRW"
          }
      }
    }
}
```

### PixelFed Verb Image liked

when the user liked an image in pixelFed environment

```javascript
{
    "actor": {
        "mbox": "mailto:usr838fh3@COURAGE.eu",
        "name": "usr838fh3"
    },
    "verb": {
        "id": "http://couragecompanion.eu/expapi/verbs/liked",
        "display": {
        "en-US": "liked"
        }
    },
    "object": {
    "id": "http://couragecompanion.eu/artifact/image/2334"
    },
    "context": {
         "extensions": {
                "http://couragecompanion.eu/expapi/context-info": {
                    "image-id": "http://closed-environment.eu/artifact/image/2334",
                    "environment":"pixelFed",
                    "vlc-time" : "1624556432999",
                    "experienceID" : "5OCTOBER2021HRW"
          }
      }
    }
}

```

### PixelFed Verb Image commented

when the user liked an image in pixelFed environment

```javascript
{
    "actor": {
        "mbox": "mailto:usr838fh3@COURAGE.eu",
        "name": "usr838fh3"
    },
    "verb": {
        "id": "https://w3id.org/xapi/dod-isd/verbs/commented",
        "display": {
        "en-US": "commented"
        }
    },
    "object": {
    "id": "http://closed-environment.eu/artifact/image/2334"
    },
    "context": {
         "extensions": {
                "http://couragecompanion.eu/expapi/context-info": {
                    "image-id": "http://closed-environment.eu/artifact/image/2334",
                    "environment":"pixelFed",
                    "vlc-time" : "1624556432999"
          }
      }
    }
}


```

...

### References

[1] https://adlnet.gov/assets/uploads/Controlled-Vocabulary-Considerations-xAPI.pdf /

https://adlnet.gov/projects/xapi/
[2]
http://xapi.vocab.pub/activity-types/index.html

https://registry.tincanapi.com/#

https://activitystrea.ms/registry/verbs/

```

```
