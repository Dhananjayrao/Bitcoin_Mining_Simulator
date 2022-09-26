# Bitcoin Mining using Erlang
COP5615 - Distributed Operating Systems Principles Project 1

## Authors
* **Dhananjaya Sathyanarayana Rao** - *UF ID: 5067 1487*
* **Dishank Murari Poddar** - *UF ID: 8049 0944*

## Size of the work unit
In this project, we aim to simulate bitcoin mining by mining sha256 encoded strings in such a way that they satisfy a stipulated condition. A server node is set up to mine the coins and is also responisble for assigning work to worker nodes as and when they are available. A worker contacts a server and participates in mining with no set limitations on the number of coins that can be mined. Messages are passed between the server and worker processes to specify the input i.e the required number of leading 0s and ensure that the server is alive while the workers are mining coins. The resultant valid coins that the workers have mined are sent to the server and displayed by the server. The number of actors issued for both server and workers, are determined by using the number of Erlang schedulars available. We have measured the performance by running 2, 4 and 8 worker nodes with peak performance measured at an 8 worker node confugration. A configuration with a higher number of processes and nodes did not yield better results. We have set the server node to stop mining upon the completion of mining a hundred coins.(Hundred is chosen arbitrarily).

## Sample Output
A snippet of the sample output on the server node for an input of k=4, with a worker node initiated on a separate node.
```
drao1;TDBrMjFnTjRqUmJFVERBbzlJNityMHRiaFpBaEhvSytKNnBTYXQycDl4QT 0000bdecbeddc98b9b638585960b850d8171c1e89a74308d54222644e516b725

drao1;dFlNRGpuQU1WenRiTUZ3cmdFb2VVZlFFT0lJVlpYdWdpWW1Vaks4MjZwUT 
0000c45114007b9c8032809ca8d780c4530e11b37e4c336334e33b4e57bbb8e9 from worker

drao1;blpMZzZEcVNKRVNQdXVGOTBUdW5DOWs4a0lEU01QTmlsMTJYTlFGVWFrdz 00009cc0ae008771f8b095c1650d3739a071154c1f174934c09d63f8e2cb8efc

drao1;NFQvVzZjaUtheTBzUlVISTBIcEl6ZzA1UjE1N2ZDRTA3cmFmSTl6NWF4OD 00000c3e5da3869226767fbd8c8c010ef3877cbc125e392f5c27b052acdd0093

drao1;VEpmUDFQQzZhOGxoS25SaDhsekQzQkFhZGdSOG82UlNUYlg4SHhLTDZXOD 0000738a846ed76cdedc583fa1c552c2b13428403342047510c9e54e4a3f3f72 from worker

drao1;amowaFg2Y090QjliV1YvMGJCNWNQNDBrQTBLRE42aEY0bWhFU0ZLRytGST 00004f2820615f7847e0d037c6bccb404e301dbb62822d7eb237cb3bd54d31a5 from worker

drao1;cVJBd0ZNd3pwN2M0bENPZFR6YXVxZmFkcE5IM0MrQXQyOEFhSUExN2szRT 0000bbdab3ac470f66508dda321ad6dd9ffd3b985f313133b2cbe3b66c55b26e

drao1;MVV0Szd5Ykd4bXNQUjdJdHpHb21NQnNKd255VHJFQU96b200aUFhUVllbz 0000eefdce6c1dc6223376e28d5eb00b99b4110f5cc0b9896847e467b8bc013e from worker

drao1;anljNXFabGFpbVFPbTZCYVNaUE9kQXpLUEJkVW9VRytuQ3JiSEpQVzhOMD 0000628a5a196060c9ddacb8b07129ae340dce5ac927295e0172e3140c6dbaf3 from worker

drao1;Mlp4VGlhZU13V0lwU0RwM3JTWkhqb0RkYjFDcnV0WlhiZ29IVWxCMjFqQT 0000677e0faa747c882daae7c620972d8d6ff037f58c45e397bd2e96d00c025d
```

## Running Time
```
The work took 83447 cpu milliseconds and 41811 wall clock milliseconds - 2 worker processes
The work took 74404 cpu milliseconds and 22739 wall clock milliseconds - 4 worker processes
The work took 93543 cpu milliseconds and 18807 wall clock milliseconds - 8 worker processes
```
## Coin with the most zeroes - 7
dishankpoddar;STlFakV5Q0V0NzZyS1RHNUxvQXVBUFlVYXc4eWpGK3haT1BzMWVLakxVaz 000000066cd1356e0de87d66aa9dc7621a55423bab1637ae28705d597024876e

## Largest Number of working machines on which the code was run
The code was run simlutaneously on 8 machines.

## Getting Started

#### Erlang
Please use Erlang >= 20.0, available at <https://www.erlang.org/downloads>.

To install on a Mac, `brew install erlang`. (you may need to `brew update` first).

Alternatively, you can also follow [these instructions](http://elixir-lang.org/install.html).

## Running
Open a terminal at the file location where the .erl files are stored.

### Run the app on a server.
```
$ erl -name servername -setcookie cookiename.
```
The name can be set to name@server-ip.

Set the name in the .erl file to name@server-ip in the 'main_node' function.

After initiating the server erlang node,
```
c(btc).
btc:start_mining().

Enter number of leading 0s for a coin: k.
```
Here k is an input that represents the required number of leading 0s to be found in the hashed string.
### Run the app on a worker.
Ensure that the compiled code (.beam file) is stored in a location such that the worker can access the server.
```
$ erl -name workername -setcookie cookiename.
```
The name can be set to name@worker-ip.

After initiating the worker erlang node,
```
btc:join_as_worker().
```
Process ids for the worker node will have been returned indicating that the worker node has begun mining in correspondence with the server.

You may also start a worker node on the same device by opening a separate terminal and setting up the name and cookie.

## Built With

* [Erlang](https://www.erlang.org/) - Erlang is a programming language used to build massively scalable soft real-time systems with requirements on high availability.
* [Visual Studio Code](https://code.visualstudio.com/) - Source code editor.






