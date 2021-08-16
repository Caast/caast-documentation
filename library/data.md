# Data

In every emitted events the following data is made available for you to interact with your environment. Exposed data is about the current live informations, your platform configuration and the current user informations. All the configuration data is customizable in your dashboard in the configuration section of your project.

The following object, is the default returned data, you will find some additional data that are merged on specific events detailed in this page.

```json
{
  "credentials": {
    "APP_ID": "7uVKGurbj0c2ca9Qp3MAUQdag7iLWWwTXc3f-KWrWSQ",
    "APP_KEY": "SP_S6EByQ50YFiSpmZS0fho8_Hg-7HsOagOmhDyxAwg"
  },
  "config": {
    "id": "7uVKGurbj0c2ca9Qp3MAUQdag7iLWWwTXc3f-KWrWSQ",
    "type": "app",
    "attributes": {
      "name": "Caast Live for Christmas",
      "uid": "7uVKGurbj0c2ca9Qp3MAUQdag7iLWWwTXc3f-KWrWSQ",
      "secret": "SP_S6EByQ50YFiSpmZS0fho8_Hg-7HsOagOmhDyxAwg",
      "redirectUri": "https://caast.tv",
      "configuration": {
        "color": {
          "button_background": "#000",
          "button_color": "#FFF",
          "header_background": "#000",
          "header_color": "#FFF",
          "product_background": "#fff",
          "product_color": "#333",
          "product_border": "#E7E7E7",
          "product_fill_buy": "#CCC",
          "product_active_background": "#fff",
          "product_active_color": "#333",
          "product_active_border": "#000",
          "product_active_fill_buy": "#000",
          "product_live_background": "#000",
          "product_live_color": "#FFF",
          "question_background": "#FFF",
          "question_border": "#000",
          "question_color": "#333",
          "question_active_background": "#000",
          "question_active_border": "#000",
          "question_active_color": "#FFF",
          "pseudo_background": "rgba(0,0,0, .05)",
          "pseudo_color": "#333",
          "chat_send_background": "#000",
          "chat_send_color": "#FFF",
          "live": "#FF015C",
          "checkbox_color": "#96e039"
        },
        "target": {
          "element": "#service-one li:nth-child(4)",
          "position": "beforeend",
          "basket": ""
        },
        "mobile_target": {
          "element": "#service-one li:nth-child(4)",
          "position": "beforeend",
          "basket": ""
        },
        "hash": {
          "question": "caast-question_",
          "jump": "caast-jump_",
          "open": "caast-open"
        },
        "mode": "mini",
        "custom_style": "",
        "custom_style_iframe": "",
        "custom_style_listing": "",
        "show_subscribe": true,
        "show_live_request": false,
        "add_to_kart": {
          "active": false,
          "url": "",
          "default_body": ""
        },
        "listing": {
          "inject_before_highlight": "",
          "inject_after_highlight": "",
          "inject_after_list": ""
        },
        "i18n": {
          "button": {
            "open": "Enter live room",
            "replay": "See replay",
            "send": "Send",
            "next": "Next",
            "prev": "Previous",
            "close": "Close",
            "hide": "Hide",
            "cancel": "Cancel",
            "validate": "Validate",
            "default": "Enter chatroom",
            "is_live": "See live"
          },
          "product": {
            "title": {
              "is_live": "A live is in progress",
              "countdown": "Live presentation in",
              "today": "A live is scheduled today at",
              "tomorrow": "A live is scheduled tomorrow at",
              "date": "A live is scheduled on",
              "no_live": "This product does not have a live presentation yet",
              "replay": "Several lives are available for this product"
            },
            "description": {
              "default": "Ask your questions now",
              "replay": "Watch them while waiting for a new live !",
              "is_live": "Enter to view the live and chat with others"
            },
            "thumbnail": {
              "is_live": "Live"
            }
          },
          "listing": {
            "title": "Lives",
            "highlight_button": "",
            "badge": {
              "is_live": "Live",
              "countdown": "Live in",
              "today": "Today at",
              "tomorrow": "Tomorrow at",
              "date": "On"
            },
            "status": {
              "all": "All lives",
              "live": "Lives",
              "replay": "Replays",
              "soon": "Soon"
            },
            "subscribe": {
              "button": "be notified",
              "title": "Be notified by email and 10 minutes before a live start.",
              "description": "By checking this, you accept our <a href='' target='_blank'>conditions</a>.",
              "feedback": {
                "email": "Mail required",
                "accept": "Please accept our conditions",
                "valid": "All is good ! You will be notified when live is about to start"
              }
            }
          },
          "subscribe": {
            "description": "Would you like to be notified before the live starts ?",
            "input_placeholder": "Enter your email",
            "success": "Registration successful! You will be notified by email of the next lives",
            "success_vote_for_live": "Thanks for your live request",
            "error": "An error has occurred",
            "error_already_mail": "You are already on the notification list"
          },
          "modal": {
            "all_lives": "All the previous lives",
            "other_questions": "Other lives questions",
            "show_questions": "Show questionss",
            "search": "Search for a question",
            "no_result_for": "No results for search {{term}}",
            "live_date": "Live from {{date}}",
            "no_questions": "Currently no questions for this live",
            "tabs": {
              "description": "Description",
              "chat": "Discussions",
              "question": "Questions",
              "product": "Products",
              "replay": "Replay"
            },
            "all_replays": "All replays"
          },
          "chat": {
            "title": "Discussions",
            "change_mode": "Click here to display only the questions during the live",
            "offline": "Chat is currently offline",
            "form": {
              "message_placeholder": "Send your message",
              "pseudo_placeholder": "Choose a nickname",
              "add_emoji": "Add a smiley",
              "as_anonymous": "Post as anonymous",
              "character_left": "{{total}} remaining characters",
              "hint_pseudo": "Cannot contain spaces and maximum 25 characters"
            },
            "message": {
              "anonymous": "Anonymous",
              "vote": "Vote for this question",
              "answered": "Question answered",
              "answered_at": "Question answered at {{time}}",
              "moderated": "Moderated content"
            },
            "emoji": {
              "search": "Search",
              "clear": "Clear",
              "notfound": "No emoji found",
              "categories": {
                "search": "Results",
                "recent": "Frequently used",
                "smileys": "Smileys & Emotion",
                "people": "Peoples",
                "nature": "Animals & Nature",
                "foods": "Food & Drinks",
                "activity": "Activities",
                "places": "Travel & Places",
                "objects": "Objects",
                "symbols": "Symbols",
                "flags": "Flags"
              }
            },
            "new_message": "View new messages"
          },
          "products": {
            "on_screen": "on screen",
            "buy_label": "Go on product page"
          }
        }
      }
    }
  },
  "lives": {
    "coming": { "data": [] },
    "current": {
      "data": [
        {
          "id": "f20aa128931a449b9478f5fb69e07c3b",
          "type": "live",
          "attributes": {
            "name": "Caast live event",
            "description": "A live event for christmas",
            "videoId": "a6b7e85c6433c00a4f1df62a1f7ec948",
            "chatId": "078a8000a55bc862c6bcf0a9cc72d9ec",
            "isStarted": false,
            "isFinished": false,
            "isDirectInsert": false,
            "startDate": "2020-12-25T20:00:00.000Z",
            "productActiveId": null,
            "productIds": ["310eb32e97044d96a5416b13fe7adf3d"],
            "productTimestamps": [
              {
                "attributes": {
                  "productId": "310eb32e97044d96a5416b13fe7adf3d",
                  "timestampEnd": 30,
                  "timestampStart": 10
                },
                "id": "49cbb03c0d594b71aceb113278f6821a",
                "type": "productTimestamp"
              }
            ],
            "products": [
              {
                "attributes": {
                  "name": "A fake product",
                  "thumbnailUrl": "https://mediadev.caast.tv/variants/...",
                  "url": "https://www.a-fake-product.com"
                },
                "id": "310eb32e97044d96a5416b13fe7adf3d",
                "relationships": {},
                "type": "product"
              }
            ],
            "thumbnailUrl": null,
            "urls": ["https://caast.tv"]
          }
        }
      ]
    },
    "passed": { "data": [] }
  },
  "user": {
    "uuid": "1d5f65e4d53b20fcb223a7dc0aec3ea0"
  },
  "userAccess": {
    "hardBan": null,
    "softBan": null
  },
  "questions": [
    {
      "id": "452159334435456999954edb1a04d779",
      "type": "question",
      "attributes": {
        "questionerName": "David Copperfield",
        "question": "What is the product price ?",
        "sentAt": "2020-12-25T21:07:57.000Z",
        "answered": true,
        "moderated": false,
        "answerTimestamp": 44
      }
    },
    {
      "id": "27bb4a0bbda54303a5a02005b19924f5",
      "type": "question",
      "attributes": {
        "questionerName": "HarryHoudini",
        "question": "Is it available in other colors ?",
        "sentAt": "2020-12-25T21:12:34.000Z",
        "answered": true,
        "moderated": false,
        "answerTimestamp": 96
      }
    }
  ]
}
```

?> _Note that the `questions` key will be missing if the modal is not yet opened._

## user

When using the [setUser](library/methods.md#setUser) method, you will add additional informations on the user object in global config, the object will now have a `custom_fields` entry in it, regrouping all the data you've provided

```json
"user": {
    "uuid": "1d5f65e4d53b20fcb223a7dc0aec3ea0",
    "custom_fields": {
        "email": "d.copperfield@abracadabra.io",
        "first_name": "David",
        "last_name": "Copperfield"
    }
}
```

The user entry can also be altered when a user set his nickname or decide to go as anonymous in the ChatRoom, you will then receive an object additional keys

```json
"user": {
    "uuid": "1d5f65e4d53b20fcb223a7dc0aec3ea0",
    "custom_fields": {
        "email": "d.copperfield@abracadabra.io",
        "first_name": "David",
        "last_name": "Copperfield"
    },
    "author": "davidCopperfield"
}

// OR

"user": {
    "uuid": "1d5f65e4d53b20fcb223a7dc0aec3ea0",
    "custom_fields": {
        "email": "d.copperfield@abracadabra.io",
        "first_name": "David",
        "last_name": "Copperfield"
    },
    "anonymous": true
}
```

## player

When listening to an event using [onLivePlay](library/events.md#onLivePlay) or [onLivePause](library/events.md#onLivePause) method, you will receive additional informations regarding the player state.

```json
"player": {
    "seconds": 36.8
}
```

## live_id

When listening to an event using [onLivePlay](library/events.md#onLivePlay), [onLivePause](library/events.md#onLivePause), [onLiveSubscription](library/events.md#onLiveSubscription), [onRelatedClick](library/events.md#onRelatedClick),[onModalTrigger](library/events.md#onModalTrigger),[onModalShow](library/events.md#onModalShow) or [onModalClose](library/events.md#onModalClose) method, you will receive additional information regarding the current live id.

```json
"live_id": "f20aa128931a449b9478f5fb69e07c3b"
```

## currentLive

When listening to an event using [onLivePlay](library/events.md#onLivePlay), [onLivePause](library/events.md#onLivePause), [onLiveSubscription](library/events.md#onLiveSubscription), [onRelatedClick](library/events.md#onRelatedClick), [onModalTrigger](library/events.md#onModalTrigger),[onModalShow](library/events.md#onModalShow) or [onModalClose](library/events.md#onModalClose) method, you will receive additional information regarding the current live.

```json
"currentLive": {
  "attributes": ...,
  "id": "f20aa128931a449b9478f5fb69e07c3b"
}
```

## question_id

When listening to an event using [onQuestionClick](library/events.md#onQuestionClick) method, you will receive additional informations regarding the question id.

```json
"question_id": "452159334435456999954edb1a04d779"
```

## product_id

When listening to an event using [onProductClick](library/events.md#onProductClick) method, you will receive additional informations regarding the product id.

```json
"product_id": "925da3518ec44b29a0cf2ed86a3610e6"
```

## product_ref

When listening to an event using [onProductClick](library/events.md#onProductClick) method, you will receive additional informations regarding the product ref.

```json
"product_ref": "128627"
```

## message

When listening to an event using [onMessageSubmit](library/events.md#onMessageSubmit) method, you will receive additional informations regarding the submitted message.

```json
"message": {
    "author": "davidCopperfield",
    "message": "Abracadabra !"
}
```

## url

When listening to an event using [onVoteForLive](library/events.md#onVoteForLive) method, you will receive additional informations regarding the current page.

```json
"url": "https://mywebsite/product/29749874"
```

## from_caast

When listening to an event using [onProductClick](library/events.md#onProductClick) method, you will receive additional informations regarding the context of the action. If this event is coming from our direct add to cart method you will receive this data.

```json
"from_caast": "true"
```
