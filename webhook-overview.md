---

copyright:
  years: 2019, 2021
lastupdated: "2021-08-25"

subcollection: assistant-data

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:external: target="_blank" .external}
{:deprecated: .deprecated}
{:important: .important}
{:note: .note}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:video: .video}

# Webhook overview
{: #webhook-overview}

Make a call to an external service or application during a conversation.
{: shortdesc}

{{site.data.keyword.conversationshort}} supports the following types of webhooks:

- Skill-level webhooks

  The following type of webhook can be set up for use from a dialog skill:

  - [Dialog](/docs/assistant-data?topic=assistant-data-dialog-webhooks)

- Assistant-level webhooks

  The following types of webhooks can be set up for an assistant:

  - [Logs](/docs/assistant-data?topic=assistant-data-webhook-log)
  - [Premessage](/docs/assistant-data?topic=assistant-data-webhook-pre)
  - [Postmessage](/docs/assistant-data?topic=assistant-data-webhook-post)

## Which type of webhook should I use?
{: #webhook-overview-difs}

The skill-level webhook is different from the assistant-level webhooks in the following ways:

- Frequency with which the webhooks is called

  The dialog webhook is called on the rare occasion that the dialog node from which it is triggered is processed.

  The message processing webhooks are called with every single exchange in a conversation between the customer and the assistant.

  The log webhook is called with each message and its corresponding response.

- Where the condition is defined

  For a dialog webhook, the condition to meet before an action is taken is defined in the dialog skill. If the node condition is not met, then the dialog webhook is never called.

  For the message processing webhooks, the condition to check for before taking an action must be defined in the external application code. For example, even if your webhook performs a simple language translation, you'd want to use a condition to check the language of the incoming message before sending the text to the translation service.

  You don't need to define a condition for the log webhook unless you want to filter the messages somehow. In most cases, the goal is to write out every message that is submitted, so the messages can be stored for as long as you want, and analyzed by an external application or service.

- Where you configure them

  You configure the dialog webhook from the the **Options>Webhook** page of the dialog skill. You then initialize it from one or more dialog nodes by customizing the node.

  You configure the assistant-level webhooks from the **Settings>Webhooks** page for the assistant.
