# Introduction
Setup an ONOS/Mininet environment for demo at Dosudo Meetup.

# Quickstart
1. Clone the repository

	```
	git clone https://github.com/rascov/dosudo-demo.git
	```
	
1. Use Docker compose to start ONOS and Mininet containers

	```
	docker-compose up -d
	```
	It might take a minute for ONOS and Mininet to be ready
	
1. Access ONOS web UI
	
	```
	http://localhost:8181/onos/ui
	```
	The default account/password is `karaf/karaf`
	Hotkeys:
	B - Toggle background map
	L - Toggle device label
	H - Toggle hosts
	
1. Open a terminal window and attach to Mininet CLI

	```
	docker attach dosudodemo_mininet_1
	```
	
1. Open a terminal window and attach to h17

	```
	docker exec -it dosudodemo_mininet_1 /root/mininet/util/m h17
	```
	
1. Ping from h17 to h5. It should fail since we have not enabled any traffic forwarding app.
	
	In h17 shell, run
	
	```
	ping 10.0.0.5
	```

1. Setup host-to-host intent between h17 and h5

	Shift-click two hosts to select and press host-to-host intent buttom on the right panel.

1. Ping again. This time it should work.

1. Tear down a switch. You should see host-to-host intent recompute the route.

	In Mininet CLI, run

	```
	switch s13 stop
	```


1. Clean up

	```
	docker-compose down
	```
