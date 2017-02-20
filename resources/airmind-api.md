
## org.airmind.ble ##

### BTLinkIO ###

> 

<pre><code><b>setBluetoothLeService</b>(BluetoothLeService bluetoothLeService)
</code></pre>

<pre><code><b>setPeerMavLinkWriteCharacteristic</b>(BluetoothGattCharacteristic peerMavLinkWriteCharacteristic)
</code></pre>

<pre><code>  To write data to specified BLE device/service/characteristic-UUID.
 @param deviceAddress BLE device-UUID
 @param serviceUUID   BLE service-UUID
 @param characteristicUUID BLE chracteristic-UUID
 @param data data to be write to connected BLE device

<b>write</b>(String deviceAddress, String serviceUUID, String characteristicUUID, byte[] data)
</code></pre>

------
### BTLinkIONative ###

> 

<pre><code> Called when data comes from connected BLE-device.
 @param deviceAddress BLE device-UUID
 @param serviceUUID   BLE service-UUID
 @param characteristicUUID BLE characeristic-UUID
 @param dataA data received from BLE-device

<b>dataArrived</b>(String deviceAddress, String serviceUUID, String characteristicUUID, byte[] dataA)
</code></pre>

------
### LinkManager ###

> 

<pre><code> Called from QT to connect to specified BLE-device.
 @param deviceAddress BLE device-UUID
 @param serviceUUID   BLE service-UUID
 @param characteristicUUID BLE charateristic-UUID

<b>connect</b>(String deviceAddress, String serviceUUID, String characteristicUUID)
</code></pre>

<pre><code>Called from QT to discover BLE devices.

<b>discover</b>()
</code></pre>

<pre><code><b>setAdapter</b>(BluetoothAdapter adapter)
</code></pre>

<pre><code><b>setBluetoothLeService</b>(BluetoothLeService bluetoothLeService)
</code></pre>

<pre><code> called when app starts up and auto-connect BLE device/service/characteristic which has
 ever been connnected before.

<b>setBluetoothManager</b>(BluetoothManager bluetoothManager)
</code></pre>

<pre><code> Called from QT to stop BLE device scanning.

<b>stopScanning</b>()
</code></pre>

<pre><code> After called {@link LinkManagerNative#tcpConnect(String, int)}, to report the connection is connected if success.
 @param host
 @param port

<b>tcpConnected</b>(String host, int port)
</code></pre>

------
### LinkManagerNative ###

> 

<pre><code> To connect BLE device specified via device parameter.
 @param device BLE device-UUID
 @param service BLE service-UUID
 @param characteristic BLE characteristic-UUID

<b>connect</b>(String device, String service, String characteristic)
</code></pre>

<pre><code> To notify discovery result.
 @param inRangeFileName full file name containing devices which meet the RSSI threshold
 @param outRangeFileName full file name containing devices which does not meet the RSSI threshold

<b>didDiscover</b>(String inRangeFileName, String outRangeFileName)
</code></pre>

<pre><code> To discover Bluetooth Lower Energy (BLE) device.

<b>discover</b>()
</code></pre>

<pre><code> On app exit, to close links matained by LinkManager.

<b>shutdown</b>()
</code></pre>

<pre><code> To stop BLE scanning.

<b>stopScanning</b>()
</code></pre>

<pre><code> To tcp-connect specified host/port.
 @param host hostname or ip-address to be tcp-connected
 @param port port number to be tcp-connected

<b>tcpConnect</b>(String host, int port)
</code></pre>

------
### ParameterManager ###

> 

<pre><code> After called {@link #refreshAllParameters()}, to report the progress of refreshing parameters.
 @param progress [0,1]

<b>parameterListProgress</b>(float progress)
</code></pre>

<pre><code> After called {@link #refreshAllParameters()}, to report paramter one by one.
 @param vehicleId aircraft's system-id
 @param componentId see MAV_COMPONENT at {@linktourl http://mavlink.org/messages/common}.
 @param mavType see MAV_PARAM_TYPE at {@linktourl http://mavlink.org/messages/common}.
        <p>
        <ul>
                <li>1 MAV_PARAM_TYPE_UINT8</li>
                <li>2 MAV_PARAM_TYPE_INT8</li>
                <li>3 MAV_PARAM_TYPE_UINT16</li>
                <li>4 MAV_PARAM_TYPE_INT16</li>
                <li>5 MAV_PARAM_TYPE_UINT32</li>
                <li>6 MAV_PARAM_TYPE_INT32</li>
                <li>7 MAV_PARAM_TYPE_UINT64</li>
                <li>8 MAV_PARAM_TYPE_INT64</li>
                <li>9 MAV_PARAM_TYPE_REAL32</li>
                <li>10 MAV_PARAM_TYPE_REAL64</li>
        </ul>
 @param parameterName
 @param parameterValue
 @param parameterIndex
 @param parameterCount

<b>parameterUpdate</b>(int vehicleId, int componentId, int mavType, String parameterName, float parameterValue, int parameterIndex, int parameterCount)
</code></pre>

<pre><code> Refresh/get all parameters from UAV.
 To get refresh progress, see {@link #parameterListProgress(float)}.
 To get updated parameter one by one, see {@link #parameterUpdate(int, int, int, String, float, int, int)}

<b>refreshAllParameters</b>()
</code></pre>

<pre><code><b>refreshAllParameters1</b>()
</code></pre>

<pre><code><b>setController</b>(IParametersController controller)
</code></pre>

------