+++
title = "Using Sieve Scripts"
layout = "howto"
hidden = true
tags = ["e-mail"]
+++

[Sieve](http://sieve.info/) is a language for filtering emails. It is used to add complex rules that cannot be added via the [filtering rules]({{< ref "e-mails/add-a-filter-rule">}}).

{{< fig "images/admin-panel_mailbox_sieve.en.png" "Administration interface: Emails - Script Sieve" >}}

The final script (with our own directives) is stored in the `$HOME/admin/mail/[domain]/[box]/filter.sieve` file in your account. You can read it to help debug your script, but you cannot edit it.

## Extensions supported

|Extension|Description|
|--- |--- |
|body|Checks the presence of one or more character strings in the email message body|
|comparator-i;ascii-numeric|Extracts numbers from the test and compares them to see if it matches|
|copy|Specifies that a copy should be used to perform the action|
|date|Performs actions based on the date/time when an email is sent/received|
|duplicate|Detects whether it is a duplicate|
|editheader|Adds or deletes text in the headers|
|encoded-character|Allows encoding special characters|
|enotify|Sends notifications|
|envelope|Assesses the envelope ("from", "to", etc.)|
|environment|Tests different labeled values in the execution environment|
|fileinto|Delivers the email to the specified folder|
|foreverypart|Allows commands to be run in all MIME parts of the email|
|ihave|Tests whether a Sieve extension is available and, if so, executes its action|
|imap4flags|Adds IMAP indicators and key words to messages|
|include|Used to include a Sieve script in another one|
|index|Used to match specific header fields by index|
|mailbox|Checks whether a specific directory exists|
|mime|Tests the specific MIME parts in the message|
|extracttext|Extracts text from MIME parts|
|regex|Uses regular expressions|
|reject|Refuses message delivery|
|relational|Allows relational comparisons|
|subaddress|Tests bounded elements in the location part of the addresses|
|vacation|Automatic answering|
|variables|Used to add variables|

{{% notice info %}}
Do not use the `require` directive, it is already included by default.
{{% /notice %}}

## Examples

-   Add a `<SPAM>` prefix to the subject of an e-mail comprising a key word to define (whether in the subject or in the body text):
    ```
    require ["editheader", "variables", "body"] ;
    if allof (
    header :contains "subject" "mot",
    header :matches "Subject" "*"
    )
    {
    deleteheader "Subject";
    addheader "Subject" "<SPAM> ${1}";
    }
    elsif allof (
    body :content "text" :contains "mot",
    header :matches "Subject" "*"
    )
    {
    deleteheader "Subject";
    addheader "Subject" "<SPAM> ${1}";
    }
    ```

---

## Links

- [Test syntax of your script](https://www.fastmail.com/cgi-bin/sievetest.pl)
- [RFC 5228](https://tools.ietf.org/html/rfc5228)