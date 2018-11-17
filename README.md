# MQTT

## NB! New config!

In order to support multiple instances and multiple servers, the configuration is totally changed! Sorry to not be backwards compatible, but I hope this solves some of the issues I have received.

Please report issues. his is not tested very much.

## Screenshot

![Screenshot](doc/MQTT.png)

Module for [MagicMirror](https://github.com/MichMich/MagicMirror/) showing the payload of a message from MQTT.

## Installasjon

Go to `MagicMirror/modules` and write

    git clone git@github.com:Utrisoft/MMM-MQTT.git
    cd MMM-MQTT
    npm install



## Configuration

Here is an example configuration with description. Put it in the `MagicMirror/config/config.js` file:

    {
        module: 'MMM-MQTT',
        position: 'bottom_left',
        header: 'MQTT',
        config: {
            mqttServers: [
                {
                    address: 'localhost',  // Server address or IP address
                    port: '1883',          // Port number if other than default
                    user: 'user',          // Leave out for no user
                    password: 'password',  // Leave out for no password
                    subscriptions: [
                        {
                        		 topic: 'home/temperature',
                        		 label: 'Temperature',
                        		 decimals: 1,
                        		 suffix: '°C'
                        	 },
                        	 {
                        		 topic: 'home/humidity',
                        		 label: 'Humidity',
                        		 decimals: 0,
                        		 suffix: '%'
                        	 },
                        	 {
								topic: 'home/boiler',
								hideValue: true,
								valueIcons: [
									{
										value: '0',
										icon: '<svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 64 64" style="enable-background:new 0 0 64 64">'+
										  '<path d="m54.13 40.06c-3.39-30.48-21.05-38.16-25.76-39.67-.56-.18-1.1.27-1.06.85.77 12.02-5.18 18.82-5.18 18.82s-7.83 9.75-10 13-5.42 15.67 3 26c7.2 8.84 15.26 2.55 17.43.55.33-.3.82-.27 1.14.04 3.61 3.56 7.79 4.48 11.43 1.41 11.41-9.61 9-21 9-21" style="fill:#b2b2b2"/>'+
											  '<path d="m32.74 59.06c0 0-5.88 5.33-10 0s-2-14-2-14 3.21-7.46 10-15c0 0 2.67-2.92 3-5 0 0 9.08 4.83 10 17 .92 12.17-9 19-9 19l-2-2" style="fill:#d8d8d8"/>'+
											  '<path d="m32.48 59.06c0 0 6.79-1.96 8-14 0 0 .88-3.88-6-10l-8 9c0 0-3 3.04-3 8s3 7 3 7 2.67 3.34 6 0" style="fill:#f2f2f2"/></svg>'
									},
									{
										value: '1',
										icon: '<svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 64 64" style="enable-background:new 0 0 64 64">'+
										  '<path d="m54 40c-3.39-30.49-21.05-38.16-25.76-39.68-.56-.18-1.1.27-1.06.85.76 12.02-5.18 18.83-5.18 18.83s-7.83 9.75-10 13-5.42 15.67 3 26c7.2 8.84 15.26 2.55 17.43.55.33-.3.82-.27 1.14.04 3.62 3.56 7.79 4.48 11.43 1.41 11.41-9.61 9-21 9-21" style="fill:#f01428"/>'+
										  '<path d="m33 59c0 0-5.88 5.33-10 0s-2-14-2-14 3.21-7.46 10-15c0 0 2.67-2.92 3-5 0 0 9.08 4.83 10 17s-9 19-9 19l-2-2" style="fill:#ff8200"/>'+
										  '<path d="m33 59c0 0 6.79-1.96 8-14 0 0 .88-3.88-6-10l-8 9c0 0-3 3.04-3 8s3 7 3 7 2.67 3.33 6 0" style="fill:#ffc800"/></svg>'
									}
								]
		                    }
                    ]
                }
            ],
        }
    }


mqttServers is an array, so you can add multiple servers to the same config. You can also use the module multiple places on the mirror/screen.

### JSON Data

If the payload contains JSON data, use the jsonpointer configuration to get the value. See [JSON Ponter specification](https://tools.ietf.org/html/rfc6901) or google an easier description.

## Collaborate

Pull requests are welcome.

## TO DO


Create a timeout, so values are deleted if they are not refreshed. May be faded out...

Create a treshold so a value is flashing if outside treshold.
