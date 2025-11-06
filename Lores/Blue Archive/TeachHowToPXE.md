# Teach how to PXE

Lesson speciale. Today's class is how to build PXE server. It happened that this time's class were filled mostly by Millenium Students

## Begin

Classroom is type Computer Lab, with lesson Network Router Switch Ultimate. Door is at right front. Teacher table is at left front. Very behind are the racks containing those Network ultimate Routers, which each student has one.

Students came to class. They are taking seats at wherever.

Students waiting for sensei to arrive. Until that, they are chatting with each other.

.

.

Sensei arrived. Sensei walk to table across room.

JOELwindows7: Afternoon, class. (continue walk to main table)... (reached, stay stand up & expect greeting), okay.

Students are sitting.

situation becomes awkwardly silent

.

.

.

Joel: (realization)?!, Oh wait, I'm not in Crossban, lmao!

few student awkward giggle

Joel: My apologies. Uh.. back when I was updating and debugging my establishment, Crossban, I... Installed this special ethics inspired from the time when I was very young. My old school had this greeting, and I guess why not implement it this to here. Because, not only it's cool, but I believe would help you my students bonds more to your senseis. Here, (raise hands), (send telepathy) here's how you guys do it.

students contemplate a bit of this special greeting mechanism. This greeting was indeed came from my old academy Tunas Bangsa from Harapan Bangsa Foundation. Before the class begin, sensei & students stand up. Following by the greeting consisting of time label greeting (e.g. Good Morning, Afternoon, or Evening), sensei honouring name (e.g. Mr. John), and God Bless you. Students sit down, and the sensei can now start the class.

Yuuka: Staand up!

all students stand up

Yuuka: Greetings.

*all*: Good afternoon, Joel sensei, God, bless, you\~\~..

Students sit down

Joel: Ah.. feels like home. Alright class, welcome. Today's class is about PXE. Now, let's warm it up. Is any of you ever heard of PXE, raise your hand?..

a student raised hand

a mob Millenium: (raise down), Isn't that a protocol used to make our computers boot from a LAN?

Joel: Correct!, S for you, and this class now, you will experience how you set it up.

*all*: Oooooo

Joel: Great, I'm glad you're excited. Now, open up File Manager now. Just open it up Aand in your Home directory we have prepared you the special files under this new folder called `PXE`. After you finished this education feel free to copy the file to your flash disk to train yourself one again, anyways.., open that directory, you'll see a couple files there.

students are examining the `PXE` folder & its content

Joel: There's your `.pxe` file, and a `.txt` file containing the information that you need to know. So, you done?

still looking

Joel: Okay, attention!

attentioned

Joel: Let me refresh you everything you need to know about PXE. PXE stands for Pre-boot Execution Environment. Again, (draw graph representing PC) it is a protocol used by the BIOS in your computer (write PXE next to the symbol `PC`) to let themselves boot by network, rather than a typical bootable disk installed on the computer. (draw smaller box graph representing Network card & another smaller one inside symbol `Network card` representing PXE Chip) How does this done is that the BIOS (draw small box inside symbol `PC` representing BIOS UEFI) goes into a special bootable disk instead of the common, usually located by its network card. (point the symbol `PXE`) This is called the PXE Chip. Once it in, now you're on a **PXE Operating System**, and it only has one goal. It's to ask if there is a boot offer who knows in their LAN, network they connected to, and once received, it execute the instruction given by whoever. Who they ask?

same mob: (raise hand) DHCP?

Joel: WOW, Another S for you!! you guys are soo..-talented! Okay then. I'm glad we got another potential IT Expert here in Kivotos. So that's correct, it's DHCP. Wait, DHCP? You class who often fiddle around with networking should no stranger, with what is DHCP, right?

Koyuki: (raise hand) It's to give computers IP Address.

Joel: That's right, an S for you. Dynamic Host Configuration Protocol is a Server Daemon with a purpose of providing IP Address for the network connectors.., Hosts, to whom they ask. It has rules one can configure, but basically the DHCP gives them IP Address for a specified amount of time in a lease. As simple as that. Nowadays, many cheap routers only had just functioning DHCP server just so device gets their IP address. And often fatally, they lose this one essential feature we need as this today's class: the `next-server`.

Students gets curious

Joel: That's right, (draw symbols representing the general infrastructure of a DHCPing with a focus to PXE booting)...., So, not-.. only.. DHCP gives... IP Addresses, ..., it also offers... a **Redirections**..., which available, for those who also asked that.. during the basic ask (asking for IP address)...... (connect the *cables*).., (finished) There. (strike a line to zoom into `next-server` topic)-So!..., a sophiscated DHCP server would have this feature that also gives instruction, called Boot Offer, if.. a Host asks for it. What you do here, is simply fill this (`next-server`) field with an IP Adddress of another server, and another field... (write `filename`).. the file the recipient should go to, once they reached the destined server.

that mob again: A file server?

Joel: Wow again!, (walk by her table) S again for you. Who.. are you? How can you be talented so about this?

mob: (embarrassed & blush) ehehehee...

Joel: Very excellent. I suggest tho, you give another students a chance..

mob: Hmm?

Joel: Okay, sorry., I digress, Yeah, (walk back to front) Good example, keep it up. So yeah, wonder what type it is? It has to be very simple. Rudimentary, but very easy for the PXE firmware to Understand.

Yuuka: (raise hand) is it TFTP? Because that's the easiest I know..

Joel: Another S for you!! that's right. TFTP is the key part of the PXE because that's how you store the PXE executable files as another Host go to. Tho, let's be honest, nowadays many shopping districts around you uses a much more advanced protocols, namely HTTP.. S (Secure), thanks to project [iPXE](https://ipxe.org), the firmware that revolutionized nalized it.. revolani.. revolutionized it all. 💢 (tongue glitch mini upset)..., Feel free to look it up if you're curious.. And.. because we're going to touch DHCP, you what that means..

*all*: Login to Router, 🎉🎉🎉🎉 yaaaaaaaaaaaaaay!!

Joel: S all for you!!! You guys are soo talented! See, you can be IT Expert in no time. Now, students, open up your browser,

student start to follow along carefully

Joel: and login to each router provided for you, which is on the second network card. Yes, that gateway there, pluged on the network card. In case you forgot it's `192`, `168`, `2`, dot `1`. Should work. Yesterday just before the schedule today, I debug test it, turning on both network cards causes confusion, so we turned the first card which goes to NAT (regular academy classroom network), ... off. Now it's just your computer, and your router. Go ahead, login.. `192.168.2.1`, and wait together.

students are redevouing to each router admin site

.

.

.

.

.

.

.

Joel: You're done? Any issues?

.

.

.

All student have rendevou'd on the site

Joel: Okay. Good. To login to this admin, (write the username template `admind_##`)..., it's `admin` dash, these two hashtags, represents YOur table number. Password is `pass` dash.. also your table number.

student start typing credential

Joel: Pad both with `zero` if before `10`. (walk to main computer), (catch up)...., (open browser), (login to router)..., (type credential)... (& enter).. (examine)...

.

.

Joel: (clear), Now after you done, just press enter, you should arrive at this screen.

students now logging in

.

.

.

.

Joel: Okay, all done?

students have arrived in dashboard

Joel: Okay, now. you'll see your router dashboard. Next, we're going to DCHP setting. I hope you remember what menu here.

student go to DCHP settings

Joel: Of course, if you forgot, this router right here, just click on the `Setting` category tab. Oh wait, make sure you use this `Manager` mode, don't go to its `Desktop` just yet. (click) `Setting`, and you should see `DHCP` right under `Network` sidebar category on the left.

.

.

.

.

Joel: Alright, is everyone of you reached `DHCP Setting`? (telepathy scan & walk around)...

.

.

.

Joel: (verified, all students has rendevou'd on DHCP setting) Good. Now, this is what makes this router worth buying. See that `PXE Boot` section down there? Click that detail-summary to open that up, and you'll see the options we need.

student saw those PXE fields and got the gists of it. So talented again!

Joel: Alright? You see those? Got the idea now? Alright simple. As you can see, your field `Boot to this server (next-server)` has been pre-filled with its own IP address, One two seven zero zero zero, or `localhost`. Why? Because another sophistication of this router is that they have **built-in file-sharing system**. It ships with 256 GB of NVMe SSD included. This model is not for NAS btw, just for quick sharing, therefore remember what we have here are the cheapest Van Elektronische routers we could find and deploy for educational use multi-numbers deployment..., anyway, there is field `and which file (filename)`, ....

follow attention

Joel: You see that this field is a File Selection field. Uh.. usually you wanna upload the `.pxe` file right now, or manually write it, both'll save automatically. So, restore your file manager window & make sure you're in `~/PXE` once again... and here's the final sophistication of this router I'm going to show you.

following

.

.

.

.

Joel: Okay, Just drag and drop both [`netboot.xyz.pxe` & `netboot.xyz.efi`](https://netboot.xyz) onto your router admin browser window, **hold it a bit!..**, wait for the response of `drop file`..., and drop it. You got this.

student drag & drop those file to the router admin

the router is receiving 2 files. They know these are a PXE & EFI files, hence putting them right on the root of share because these files usually fetched without directory in between.

.

.

.

Joel: Done?

some students: 👍!..

Joel: Okay?.. You should be able to catch this up, it's very easy.., You'll see the notification on the bottom left of its admin window, and once done, just click `browse` on this file select field, and select that `.pxe` file just been placed. It should be there. This router is smart, it is aware that if you upload a bootable file, it would place it right on the root of the file share.

.

.

.

Joel: ANd that is all. Once done, Just enable `PXE Boot` now, (demonstrate) like this, you'll receive confirmation to enable `TFTP`, just click `Yes`, and wait until its [`copyparty`](https://github.com/9001/copyparty) is restarted, because you have enabled a new protocol and the best thing here it only need to restart just the file sharing system, not the whole router. Very cool right?. Okay. Now this is the rendevouz. I'll wait you there. If you need help, don't hesitate to call me?

.

.

.

Joel: Yuzu? You following?

Yuzu: 👍..

Joel: Okay. But I need to make sure. (walk to Yuzu's table in backmost right corner) I'm afraid you might've missed the whole thing. ...... (arrive), May I?

Yuzu: (slide back to give sensei space)!...

Joel: (check overall PXE fields)... okay.. (click `browse`).... (both bootable files are there & the `filename` field is already correct)... Okay good, (clap)!!,

Joel: (return back to front stage while carefully scan the status of rests of the students)... ... ...

Yuzu: (restore sitting)...

.

.

Joel: Okay, looks like you have arrived. Now at this point, your PXE server Is ready. How do you test if it works? You cannot restart this computer because that's inefficient, you what that means?

*all*: Virtual Machine time!!

Joel: S to all of you!!.. Alright, So, we have a virtual machine on this computer, we're going to use [VirtualBox](https://virtualbox.org). Uhm yeah, this was so hard to setup, we were supposed to use [QEMU](https://qemu.org) here, but.. doesn't have PXE ROM in it. Therefore netbooting by ISO just makes it redundant. SOoo, we'll use VirtualBox, open it up,

students start VirtualBox. It's also right in the app menu

Joel: why virtual box? It has iPXE that's too stripped down to be considered complete. Might what we need to demonstrate the loop to netboot as much as possible, you got the idea. Right. As you can see on the window, we already have setup the virtual machine called `PXE Boot` just for you to try. ... (nervous this won't gonna work)...

.

.

.

.

Joel: Okay, just start that machine up..

students start VM `PXE Boot` at the same time

.

.

.

.

Joel: Alright... I hope we reach netboot here.. pls....

.

.

DHCP offer received from router. all

Joel: Huh, wait..

Booting Netboot.xyz

Joel: (check connected disks & `Preferences`) wait did I... (only `Network` is ON)... Oh wow it works. Haha... ha.. idk how did it works (press ⬇️ once to stop timeout), (contemplate)....., (now check the students) Okay, (walk to the Yuzu and scan) Class, .... if you have reached the netboot menu, press the arrow key once, to remove its timeout now. Uh... ... .. We're going to see... (all works) Oh wow. everyone's work. . This is even confusing. (return to stage) Okay then, set your selection to `FreeDOS`..... (arrived) like this (arrow set selection to `FreeDOS`).. (Okay). Okay, just stay there.

.

.

.

.

Joel: Okay. You all there? Hands on the Enter button, and we'll press Enter together. Note this, on my mark, Press twice. Got it? ..

*all*: got it

Joel: Alright here we go, 3, 2, 1, Enter!, Enter!.

Downloading FreeDOS Full installer

.

.

.

.

.

.

One has reached screen

another another mob: Okay, what next?

Joel: You're there? Good!

main table reached

Joel: Okay. Now, at this point, once we have reached the installation, we are done here. That's it. Now the OS has loaded on your RAM and it's ready to use. Well, if you want to fiddle around the installation, go head, but let's not, coz it's long, .... (action) instead we are going to exit. Right, just exit to prompt., (pause projector)

.

.

.

.

.

Noa: (exited to DOS prompt), (recontemplate) That's it? Wow that was easy.

Joel: Yep.., thankfully it works. I was really afraid we shouldn't do this class, coz this is very niche. However I found that even System Information subjects here on yOUr Millenium, somehow forgot to teach this one. I mean.. you got alot of computers going on, surely you gotta know how, that's why.

Noa: Okay.. hmmm...

.

.

.

Joel: Okay class, we are DONE!. I'm gonna show you the bonus content, so I recommend you pay attention to this one. (unpause projector) I have here (turn off this virtual machine & go take a look at `Strangely Setup PXE sample`)......, holdon, network (switch the Ethernet back to main)....., Uh btw, you don't have to follow this but... This `Crossban WiFi` right here has PXE. (turn on the machine) That's right. The DHCP server on every Crossban will have Netboot. So if you require OS installation or Recovery something, just connect to this network, plug in ethernet cable around this building, and our DCHP server will serve you the boot. Wow, look at this talented sysAdmin responsible in this Crossban just a week ago.

Netboot has arrived. Go ahead try `Tinycore` Live CD.

.

.

.

.

.

Joel: I know it's silly, but who knows. Our library too has dangling ethernet cable on spare computer desk. Formerly used to hold borrowable PC, but now's empty and we restored the cable dangling just for this exact reason. Coz guess what? WiFi can be succ more that connect. And turns out, this is the best idea to put PXE also. I'm wondering. If you guys could make PXE connects wirelessly. Like.. boot agnostic. A pre-electronic networking card, which has a mini computer solely connect to WiFi and bridge it out, **emulating it as if your computer connected by cable**. I guess this is trivial theory, but idk how the bridging could be done. That's your bonus, but don't force yourself to it.. no reward for this one.

TinyCore has started

Joel: Tho, as always, if you really did that, I encourage all of you class, **to share it**. How it's done. Okay.

Time's up

Joel: Yep times up, pls stay on your seat space, it's verifying.............

All students are here

Joel: Great job! You are all online!

Koyuki: Huh? What was that?

Joel: Oh yess. Student Attendance verification technology. Inspired by my old college at Binus. Every classroom has (point) this RFID antenna that scans all card in this room realtime, much like Casino Chip RFID counter. Yep, 2 wireless, Near & Far. The Far gets you the student number in the card. Near is when you (point offer) tap that scanner by the door there. Don't worry if you forgot, the RFID will be the final judge for it, so if you forgot your card, intentionally left the class before verification, you're done for. Never dare to cheat on this. I know it's "*Privacy Invasion*", but hey, we are in Academic. All that scanning is just for academics. That's your UID of this Crossban and where are you at. And this Academy since the beginning uphold strict discipline, I trust you know the basic. Alright, Farewell!,

Yuuka: Stand up!,

all stand up

.

.

Yuuka: Greetings..

*all*: Good afternoon, Joel sensei, thank you and God Bless you\~

Joel: (run script to open PNG of QR code download same resource again)!, Alright you're doing great job in this class. (tidy up) No homework today, coz you're abroads in the Crossban. Aaand, if you'd like to download the same resource complete with bonus questionaires, here's the QR code, to our GitHub folder to it. And Thancc.., for your attention. (leave)

## Boot it up

by JOELwindows7
Perkedel Technologies
CC4.0-BY-SA

## Extras

Sensei & few Prominent Millenium Students are experimenting Speaker over IP. use [NanangMrk's YouTube video](https://youtu.be/EA4PdpRUF-Q) as an inspiration

A rig of SoIP. This demonstration rig is a setup of applied Mumble setup as SoIP system.
There is a small computer acting as a server for the whole SoIP. This server runs Mumble server daemon, Mumla, which a server called `SoIP` was setup with its authentication.
Next, a speaking client. This client computer runs Mumble that connects to the Mumla back to the server there. It has a USB Microphone connected to it. The USB Microphone has a couple keyboard keys: large orange `F1` as a PTT, and 3 customizable buttons upon: `F2`-`F4`. The client has configured to listen to `F1` hold key as PTT.
Another client, a speaker client. This client also connects to that Mumla over there. It lacks Microphone however, but instead a loudspeaker. When one of the talker talks, its audio will be outputted to all clients that has speaker connected.
And finally, two-way client. This client once again connects to the Mumla over there. It has a telephone handset which basically is just handsfree shaped like telephone. Lifting up handset has selectable dip switches to actions: Hold `F1`, Unmute (internal), unlatch end call (hence put handset preses `end call` & lift is `answer` intent button). it is set to `F1` & `Unmute (internal)`.

Joel: Okay, is it done?, (press `PTT`) Roger roger,

delay 500 ms

Joel: this is DNB Zero hello world, over (release). Right it works. So.. this is how SoIP is basically built. We can pick up components off the shelfs. It's much cheaper, and infact relies by the reliability of say, Ethernet cables wired up throughout the building.

students excitedly understood

Joel: Alright, go ahead if you wanna try..

Koyuki excitedly grab

Joel: Whoa okay.. take it easy

Koyuki: Okeh, (hold `PTT`)!, Roger roger!...

view outside, to the Millenium campus building. The whole Nihaha voice & even Joel's sexy voice heard across whole Kivotos unreazingly, this whole time!!

Koyuki: Thanks Joel sensei for helping me out this IT homework, Nihahahahaaa!..., over!-(release)!

Joel: Okay. That's all about it. You should be able to fill this out easily. And if your classmate got into difficulty, remember., **Assist, not walkthrough.** Got it?

Koyuki: (attempt to speak Bahasa Indonesia) Siap bosku!

Joel: Okeh (offer give me five) man (async)tap!

Koyuki: (async) (FIVE)!!!

Joel: (relook the rig). ... (something's off on that Server)... wait..

fade in the chase music

Joel: (examine)... (the Power LED is down, press `Power`)?..

Server turns on. heavy metal thunk

Joel: Oh frick!, (quickly VNC to the Mic client)... (yep, the Mumble connects to the Master Millenium Mumla Server this whole time)!??!!!

music beat drop. Yep, sensei got screwed up real bad. Now Wakamo is otw!!

Students are filling out report

Joel: Uh, class.. we're done here. Tho, it's next week, great job on you doing it now and leaving it complete. No extra rewards, but appreciated. (check situation)... Class dismissed, (open portal)!, Thank you and God Bless you. (jump)!-(close portal)!

Wakamo is on the building

Wakamo reaches the 17th floor

Wakamo crash breaks the door jeger!!!

Wakamo: Sensei!!... I know you're heeeere!... Come out and play with mee!

Yuuka: Sorry, he left. You're 10 step too late, be faster next time.

Wakamo: Aww 😔...

Yuuka: Also, (open portal underneath Wakamo's feet)!

Wakamo: HUAAAHAaAhA!!

Yuuka: (close)!, back to your cell.

Wakamo: Oof!! aaargh... Ouchie... that was rude! 💢 hmph!...

## Extras 2

Yuuka: SensEEEEEEEEEEEEi!!

Joel: Oh crap.. you caught me again.. .., Congratulations.

Yuuka: 💢💢💢💢💢 Ugh! I'm tired of telling you this countless times. You handle it yourself, now!..

Joel: Oh c'mon. The character here is limited!, I'm running out of time, This is collab character.

Yuuka: Didn't I tell you, stop playing Gacha games? I thought we agreed to do this.

Joel: Wait. Who said this is Gacha game?

Yuuka: Huh??, (look at phone)....

a digital item is going to be discontinued. This is not Gacha game. A Paid game. There is this DLC, that is purchase will be disabled in time.

Joel: That's everyone's mission. One down only grow 2, not only good, but also evil.

Yuuka: (Internal Flabbergasted, accidentally involved into the deep rabbithole level of Scandal fighting mission) Uhaaa....., (wake up) But..

Joel: I know. But just in case.
