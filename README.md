# BBB Sipgate Ansible Role

This role adds a callin option via sipgate/sipgate trunk and should be easily extendable to other sip provider.

## Options

The follwing options are available. Only sipgate_username, sipgate_password and sipgate_call_number need to be set for sipgate basic (and team?). For sipgate trunk see the section below that.

- sipgate_gateway_name: sipgate.de
  The SIP server to connect to.
- sipgate_proxy_value: {{ sipgate_gateway_name }}
- sipgate_username: ""
  The sip username (Note: This is not the username of you )
- sipgate_password: ""
  The sip password (NOTE: This is not the password of you sipgate account)

- sipgate_destination_number: "^{{ sipgate_username}}"
  Freeswitch only accepts calls where the destination number matches this.
  For sipgate basic (and team?) this is the username, for sipgate trunk see below

- sipgate_call_number: ""
  This number will be shown as a call-in number to the user.
- sipgate_footer: "<br><br>To join this meeting by phone, dial:<br>  %%DIALNUM%%<br>Then enter %%CONFNUM%% as the conference PIN number."
  If this is set, the `defaultWelcomeMessageFooter` will be set to this value.

## Sipgate trunk

If you have a sipgate trunk account and correctly configured a trunk, set the following options in addition to those above:

- sipgate_gateway_name: sipconnect.sipgate.de
- sipgate_destination_number: the number the user called including the country prefix (for example "49301234567")
