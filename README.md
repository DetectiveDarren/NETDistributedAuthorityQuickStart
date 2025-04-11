*Explica aquí os métodos e variables dos seguintes scripts:
 
 - ConnectionManager.cs
 _profileName: almacena el nombre del perfil del jugador.
 _sessionName: almacena el nombre de la sesión a la que se desea conectar o crear.
 _maxPlayers: define el número máximo de jugadores en la sesión (por defecto, 10).
 _state: enumera el estado actual de la conexión (Disconnected, Connecting, Connected).
 _session: referencia a la sesión actual de tipo ISession.
 m_NetworkManager: referencia al componente NetworkManager adjunto al mismo GameObject.
 Awake(): inicializa el servicio de Unity, asigna el NetworkManager y registra los callbacks para eventos de conexión y promoción de propietario de sesión.
 OnSessionOwnerPromoted(): se llama cuando el propietario de la sesión es promovido; verifica si el cliente local es el nuevo propietario.
 OnClientConnectedCallback(): se ejecuta cuando un cliente se conecta; verifica si el cliente local está conectado y puede generar objetos de red.
 OnGUI(): dibuja la interfaz gráfica para ingresar el nombre del perfil y de la sesión, y un botón para crear o unirse a una sesión.
 OnDestroy(): abandona la sesión actual al destruir el objeto.
 CreateOrJoinSessionAsync(): maneja la lógica asincrónica para autenticarse, crear o unirse a una sesión con los parámetros proporcionados.
 
 - PlayerCubeController.cs
 Speed: define la velocidad de movimiento del jugador.
 ApplyVerticalInputToZAxis: indica si la entrada vertical se aplicará al eje Z en lugar del eje Y.
 m_Motion: almacena el vector de movimiento basado en la entrada del jugador.
 Update(): solo ejecuta el código si el objeto está generado en la red (IsSpawned) y el cliente tiene autoridad sobre él (HasAuthority). Captura la entrada del jugador usando Input.GetAxis("Horizontal") para el eje X y Input.GetAxis("Vertical") para el eje Y o Z, según el valor de ApplyVerticalInputToZAxis. Si hay movimiento (m_Motion.magnitude > 0), actualiza la posición del cubo multiplicando el vector de movimiento por Speed y Time.deltaTime.
 
 *Explica os seguintes compoñentes do GameObject `NetworkManager`:
 
 - Network Manager: es el componente que maneja el estado de red en un juego multi-jugador.
 
 - Unity Transport: es el transporte recomendado que maneja la transmisión de datos entre el cliente y el servidor.
 
 - Connection Manager: es el script "ConnectionManager.cs", proporciona la UI para ingresar el nombre del jugador y la sesión y maneja la lógica para autenticarse y conectarse a una sesión.
 
 
 *Explica os seguintes compoñentes do Prefab `PlayerCube`:
 
 - Network Object: permite que el objeto sea reconocido y gestionado por el NetworkManager, asegurando que su estado se sincronice correctamente entre el servidor y los clientes.
 
 - Player Cube Controller: es el script "PlayerCubeController.cs", gestiona la lógica de movimiento del cubo del jugador en función de la entrada del usuario, permitiendo que el jugador controle su cubo en la escena.
