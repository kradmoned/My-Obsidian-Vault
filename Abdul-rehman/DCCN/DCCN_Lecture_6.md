# SMTP

- Simple main transfer protocol
- Utilizes port 25.
- IT Utilizes TCP,
- For retrieval of mails from male server IMAP(Internet message access protocol), POP3(Post Office protocol 3)
- Forward email among mail server.

## Actors

- User Agent such as gmail.
- Every company has its own mail server. SUch ar yahoo, gmail.
- Protocol such as SMTP(SMTP is only for sending).

## Working

user uses smtp-> M.S such as gmail. uses SMTP -> M.s Such as hotmail uses POP3/IMAP. -> To another user.

## Receiving protocol

- IMAP.
- POP3.

| Pop3                                  | IMAP                                                                                                            |
| ------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| After downloading the mail is deleted | Install a software in your machine such as outlook and configure it, go to the mail server and fetch your mails |

## PRos and cons of POP3

### CONS

- Does not sync folder

### PRos

- No copy is manufactured
- No space limit

## Pros and cons of IMAP

### CONS

- USe storage

### PRos

- Is synced

## Questions

### 1. If mail is opened via POP3, can IMAP still get it?

**Generally No.** By default, POP3 **downloads and deletes** the mail from the server. Once it is deleted from the server, the IMAP client (which mirrors the server) will see nothing.

- _Exception:_ If you specifically check the setting "Leave a copy of messages on server" in your POP3 client, then IMAP can still retrieve it.

### 2. If mail is deleted via IMAP, can POP3 still get it?

**No.** IMAP stays synced with the server in real-time. If you delete a mail via IMAP, it is removed from the server immediately. When your POP3 client eventually checks for mail, that message is already gone.

### 3. Does a received mail imply it was pushed to POP3?

w**No.** POP3 is a **"Pull" protocol**, not a "Push" protocol. Even if the mail server has the email, the User Agent (like Outlook or Thunderbird) will only fetch it when the user manually clicks "Send/Receive" or when a pre-set timer (e.g., every 15 minutes) triggers a request.

---

### Summary Table

| Action            | Impact on Server    | Impact on Other Protocol                            |
| :---------------- | :------------------ | :-------------------------------------------------- |
| **POP3 Download** | Usually deleted     | IMAP sees nothing                                   |
| **IMAP Delete**   | Deleted immediately | POP3 cannot find it                                 |
| **Mail Arrives**  | Sits on server      | Waiting for Agent to "Pull" (POP3) or "Sync" (IMAP) |

# DNS Khud karni
