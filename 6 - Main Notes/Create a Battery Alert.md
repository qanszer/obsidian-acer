
2025-09-14  18:48

Tags:  [[Terminal]] [[Customization]]

# Create a Battery Alert

This is for only for Linux OS

1. Open terminal:  ctrl + alt + t
2. Type:  nano battery-alert.sh
3. Paste this script:
	#!/bin/bash

	HIGH_THRESHOLD=80  # Alert to unplug
	LOW_THRESHOLD=30   # Alert to plug in
	ALERT_SOUND="/usr/share/sounds/freedesktop/stereo/alarm-clock-elapsed.oga"
	
	# Flags to prevent repeated alerts
	high_alert_sent=false
	low_alert_sent=false
	
	while true; do
	    battery_info=$(upower -i $(upower -e | grep BAT))
	    battery_level=$(echo "$battery_info" | grep percentage | awk '{print $2}' | tr -d '%')
	    status=$(echo "$battery_info" | grep state | awk '{print $2}')
	
	    # --- Alert to unplug at high threshold ---
	    if [ "$status" = "charging" ] && [ "$battery_level" -ge "$HIGH_THRESHOLD" ]; then
	        if [ "$high_alert_sent" = false ]; then
	            notify-send "🔋 Battery Alert" "Battery is at ${battery_level}%. Please unplug to protect battery health."
	            paplay "$ALERT_SOUND"
	            high_alert_sent=true
	        fi
	    else
	        # Reset the high alert flag once it goes below the threshold
	        if [ "$battery_level" -lt "$HIGH_THRESHOLD" ]; then
	            high_alert_sent=false
	        fi
	    fi
	
	    # --- Alert to plug in at low threshold ---
	    if [ "$status" = "discharging" ] && [ "$battery_level" -le "$LOW_THRESHOLD" ]; then
	        if [ "$low_alert_sent" = false ]; then
	            notify-send "⚠️ Battery Low" "Battery is at ${battery_level}%. Please plug in your charger."
	            paplay "$ALERT_SOUND"
	            low_alert_sent=true
	        fi
	    else
	        # Reset the low alert flag once it goes above the threshold
	        if [ "$battery_level" -gt "$LOW_THRESHOLD" ]; then
	            low_alert_sent=false
	        fi
	    fi
	
	    sleep 60
	done

4. Execute the command:  chmod +x ~/battery-alert.sh
5. Automate it by opening the app called "Startup Applications"
6. Add program and enter these:
	Command: /bin/bash/home/(yourusername)/battery-alert.sh
7. Reboot your laptop. It should work now.



# References


