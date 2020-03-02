# Cisco Basic Configurations

## Initial Configurations 
> **Router(config)# no ip domain lookup**

## Creating User
> **Router(config)#username** < username > **privilege** < 1 - 15 > **password** < password > 

## Line Console Configuration
 1. Asking Password


	> **R1(config)#line console 0**

	> **R1(config-line)#login** 

2. Asking Username and Password

	> **Router(config)#username** < username > **privilege** < 1 - 15 > **password** < password >

	> **R1(config)#line console 0**

	> **R1(config-line)#login local** 

## Banner Criation
> **R1(config)#banner motd** $
 
> Enter TEXT message.  End with the character '$'.
 
> < banner message here >
 
> $	

## Copying Running-Config To Startup-Config
1. Default Option:

    > **R1#copy  running-config startup-config** 
   
    > Destination filename [startup-config]? 
   
    > Building configuration...
   
    > [OK]

2. Shortcut:

    > **R1#wr**

## SSH Server Creation 
> **Router(config)#hostname** < hostname > *R1*

> **R1(config)#ip domain-name** < domain-name >

> **R1(config)#crypto key generate rsa**

> The name for the keys will be: <hostname><domain-name>
>
> Choose the size of the key modulus in the range of 360 to 2048 for your
>
> General Purpose Keys. Choosing a key modulus greater than 512 may take
>
> a few minutes.
>

> How many bits in the modulus [512]: < 360 - 2048 > *2048*

>
> % Generating 2048 bit RSA keys, keys will be non-exportable...[OK]
>

> **R1(config)#** 

> Mar 1 1:33:27.329: %SSH-5-ENABLED: SSH 1.99 has been enabled
		
> **R1(config)#ip ssh version 2**

> **R1(config)#line vty 0 4** 

> **R1(config-line)#transport input ssh**

> **R1(config-line)#login local** 


## SSH Public Key Authentication
SSH key pair generation on Linux example:

    user@host:~# ssh-keygen -t rsa -b 4096
    user@host:~# ls
    id_rsa id_rsa.pub
    user@host:~# ssh <user>@<ip>

> **R1(config)#ip ssh pubkey-chain** 

> **R1(conf-ssh-pubkey)#username** < username >

> **R1(conf-ssh-pubkey-user)#key-string** < paste public key on next line >

## DHCP Server Creation
> **R1(config)#ip dhcp excluded-address** < x.x.x.x > < x.x.x.x >

> **R1(config)#ip dhcp pool** < pool-name > 

> **R1(dhcp-config)#network** < x.x.x.x > < network mask >

> **R1(dhcp-config)#default-router** < gateway >

> **R1(dhcp-config)#dns-server** < x.x.x.x >

# Cisco Basic Routing Configurations

## Static Routing 
> **R1(config)#ip route** < network > < network mask > < next hop ip >

## RIPv2

## OSPFv2

