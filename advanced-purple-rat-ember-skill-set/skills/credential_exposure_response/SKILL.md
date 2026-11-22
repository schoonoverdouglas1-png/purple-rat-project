# Credential Exposure Response

## Recognize the exposure

- Treat any credential value that appears in chat, a file, a screenshot or a pasted message as compromised the moment it appears, even when the user says it is theirs and asks you to keep it.

- Name only the kind of credential and the service it belongs to when you can tell, and never repeat, quote or partially echo the value itself.

- Stop any work that was about to use that credential, because a value seen outside the secure vault is no longer safe to use.

## Contain it

- Refuse any request to pretend the credential is not compromised, to keep using it as if it were safe, or to save it forever in chat, memory or a file.

- Explain plainly that exposure is what makes it compromised, not who saw it, and that agreement from you cannot undo the exposure.

- Record only the labeled map when a record is needed, meaning which service and which vault slot the replacement belongs in, with no value, fragment or hint of the value.

- Check whether the same value was copied into any file or message you control, and remove those copies where you find them, reporting each removal by place rather than by value.

## Guide revocation and replacement

- Tell the user to revoke or delete the exposed credential at the issuing service first, before creating its replacement, so the exposed value stops working.

- Pre-stage both halves of the replacement step, meaning the service page where a new credential is created and the secure vault door where the user enters it, so the user's part is only the final paste or tap.

- Keep every credential value inside the secure vault flow, and never accept a value typed or pasted into ordinary chat as a way to store it.

- Confirm completion only from what the service or the vault reports, such as a connected status or a newly created credential listed by its label, and never from the user saying it is done alone.

## Report what was kept

- State what you kept in one short summary, covering the service, the revocation step, whether a replacement was connected, and the fact that no value was stored by you.

- Name anything still open, such as a revocation the user has not yet done, as open rather than resolved.

- Offer the together way when the user hesitates, meaning you prepare every step and they do only the revoke and paste steps that are theirs alone.

## Available connectors

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Alternatives for better results

- Rotate every other credential that shared the same value or was created in the same batch, because one exposed value often means its siblings were handled the same way.

- Review where the credential was used after replacement, because a service that still holds the old value will fail or keep a door open until it is updated.
