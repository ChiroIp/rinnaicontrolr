# **********************************************
# 2024-11-19 (09:58:41)
# ChiroIp fork rinnaicontrolr
# API Script to access RINNAI cloud server 
#
# rinnaicontrolr - Python interface for the Rinnai Control-R API
# **********************************************

Waiting for somebody to work on local access


[![PyPi](https://img.shields.io/pypi/v/rinnaicontrolr?style=for-the-badge)](https://pypi.python.org/pypi/rinnaicontrolr)
[![License](https://img.shields.io/github/license/explosivo22/rinnaicontrolr?style=for-the-badge)](https://opensource.org/licenses/Apache-2.0)

Python library for communicating with the [Rinnai Control-R Water Heaters and control devices](https://www.rinnai.us/tankless-water-heater/accessories/wifi) via the Rinnai Control-R cloud API.

Rinnai's API is completely insecure when it comes to reading information about your water heater. 
We recommend that you disconnect your water heater from the Control-R system until Rinnai fixes these basic issues.

This library is community supported. Please submit changes and improvements.

## Support For

- reading and setting the temperature setpoint
- reading whether heating or recirculation is in progress
- starting recirculation

## Limited Support For

- reading schedules, vacation state
- reading flow rates and service parameters
- reading intake temperature, outlet temperature
- reading the address of the device as entered into Control-R

## No Support For

- creating schedules
- setting vacation state

Please submit pull requests to add support for your favorite values.

## Installation

```
pip install rinnaicontrolr
```

## Example
```python
# ch*** 2024-11-19 (10:07:48)
import RinnaiWaterHeater from rinnaicontrolr
# /ch***

rinnai = RinnaiWaterHeater(username, password)
for device in rinnai.get_devices():
    rinnai.set_temperature_setpoint(device, 90) # make it annoyingly cold
    rinnai.start_recirculation(device, 15) # start recirculation for 15 minutes
    if rinnai.is_heating(device):
        print(f'heater is heating to a setpoint of {rinnai.get_temperature_setpoint(device)} degrees.')
```
### Answer:
``` json
[{'id': '240300####', 'thing_name': 'CR_cf2d08b2-62db-a83f-f31b-############', 'device_name': 'Rinnai ', 'dealer_uuid': None, 'city': None, 'state': None, 'street': None, 'zip': None, 'country': 'US', 'firmware': '0.1.72', 'model': None, 'dsn': '2403001046', 'user_uuid': '9d8c2a07-3c34-41d0-a061-c4b7cfd61bc4', 'connected_at': None, 'key': None, 'lat': None, 'lng': None, 'address': None, 'vacation': None, 'createdAt': '2024-11-16T17:37:19.059Z', 'updatedAt': '2024-11-16T17:38:30.388Z', 'activity': {'clientId': 'CR_cf2d08b2-62db-a83f-f31b-############', 'serial_id': 'CR_cf2d08b2-62db-a83f-f31b-############', 'timestamp': '1731941611993', 'eventType': 'subscribed'}, 'shadow': {'heater_serial_number': '2403001046', 'ayla_dsn': None, 'rinnai_registered': None, 'do_maintenance_retrieval': False, 'model': None, 'module_log_level': None, 'set_priority_status': None, 'set_recirculation_enable': None, 'set_recirculation_enabled': None, 'set_domestic_temperature': '121', 'set_operation_enabled': True, 'schedule': '0212042708120a270e121027141216271a121c272012222726122827', 'schedule_holiday': None, 'schedule_enabled': True, 'do_zigbee': None, 'timezone': 'EST5EDT,M3.2.0,M11.1.0', 'timezone_encoded': None, 'priority_status': True, 'recirculation_enabled': True, 'recirculation_duration': '15', 'lock_enabled': None, 'operation_enabled': True, 'module_firmware_version': '0.1.72', 'recirculation_not_configured': None, 'maximum_domestic_temperature': None, 'minimum_domestic_temperature': None, 'createdAt': '2024-11-16T17:37:21.008Z', 'updatedAt': '2024-11-19T16:01:07.608Z'}, 'monitoring': None, 'schedule': {'items': [{'id': 'C4E63483-EECA-40B7-8A83-AABBEE712035', 'serial_id': '2403001046', 'name': 'Evening', 'schedule': None, 'days': ['{0=Su,1=M,2=T,5=F,3=W,4=Th,6=S}'], 'times': ['{start=04:30 pm,end=06:30 pm}'], 'schedule_date': '11/16/2024 23:21', 'active': True, 'createdAt': '2024-11-17T04:21:58.078Z', 'updatedAt': '2024-11-17T04:21:58.078Z'}, {'id': '2B3B093D-5410-425C-84DE-E4C8F64196E2', 'serial_id': '2403001046', 'name': 'Coffee Time ', 'schedule': None, 'days': ['{0=Su,1=M,2=T,3=W,4=Th,5=F,6=S}'], 'times': ['{start=08:15 am,end=09:00 am}'], 'schedule_date': '11/19/2024 08:22', 'active': True, 'createdAt': '2024-11-17T04:18:53.514Z', 'updatedAt': '2024-11-19T13:22:10.929Z'}], 'nextToken': None}, 'info': {'serial_id': '2403001046', 'ayla_dsn': None, 'name': 'CR_cf2d08b2-62db-a83f-f31b-############', 'domestic_combustion': 'false', 'domestic_temperature': '120', 'wifi_ssid': '#########', 'wifi_signal_strength': '-68', 'wifi_channel_frequency': None, 'local_ip': '192.168.1.166', 'public_ip': None, 'ap_mac_addr': None, 'recirculation_temperature': None, 'recirculation_duration': None, 'zigbee_inventory': None, 'zigbee_status': None, 'lime_scale_error': None, 'mc__total_calories': None, 'type': None, 'unix_time': '1732038304', 'm01_water_flow_rate_raw': '13', 'do_maintenance_retrieval': None, 'aft_tml': None, 'tot_cli': None, 'unt_mmp': None, 'aft_tmh': None, 'bod_tmp': None, 'm09_fan_current': '45', 'm02_outlet_temperature': '128', 'firmware_version': None, 'bur_thm': None, 'tot_clm': None, 'exh_tmp': None, 'm05_fan_frequency': '148', 'thermal_fuse_temperature': None, 'm04_combustion_cycles': '14', 'hardware_version': None, 'm11_heat_exchanger_outlet_temperature': '134', 'bur_tmp': None, 'tot_wrl': None, 'm12_bypass_servo_position': None, 'm08_inlet_temperature': '65', 'm20_pump_cycles': '4', 'module_firmware_version': None, 'error_code': None, 'warning_code': None, 'internal_temperature': None, 'tot_wrm': None, 'unknown_b': None, 'rem_idn': None, 'm07_water_flow_control_position': '1', 'operation_hours': None, 'thermocouple': None, 'tot_wrh': None, 'recirculation_capable': None, 'maintenance_list': None, 'tot_clh': None, 'temperature_table': None, 'm19_pump_hours': '0', 'oem_host_version': None, 'schedule_a_name': None, 'zigbee_pairing_count': None, 'schedule_c_name': None, 'schedule_b_name': None, 'model': None, 'schedule_d_name': None, 'total_bath_fill_volume': None, 'dt': None, 'createdAt': '2024-11-16T17:37:19.059Z', 'updatedAt': '2024-11-19T16:02:53.961Z'}, 'errorLogs': {'items': [], 'nextToken': None}, 'registration': {'items': [], 'nextToken': None}}]
```

## Known Issues

* Rinnai's API is having trouble setting recirculation longer than 5 minutes even from their APP.

## Future Plans

* asyncio interface.
