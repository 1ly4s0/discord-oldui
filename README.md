## Método para volver a la antigua UI de Discord

Cómo utilizar este código:
1. Ve a https://discord.com/app
2. Presiona `Ctrl + Shift + I` para abrir el DevTools
3. Ve a la pestaña `Console`/`Consola`
4. Pega el siguiente código y presiona enter:

```js
let wpRequire;
window.webpackChunkdiscord_app.push([[ Math.random() ], {}, (req) => { wpRequire = req; }]);

let UserSettingsActions = Object.values(wpRequire.c).find(x => x?.exports?.PreloadedUserSettingsActionCreators).exports;
let ProtobufTypes = Object.values(wpRequire.c).find(x => x?.exports?.BoolValue).exports;

UserSettingsActions.PreloadedUserSettingsActionCreators.updateAsync("appearance", data => {
    data.mobileRedesignDisabled = ProtobufTypes.BoolValue.create({value: true})
}, UserSettingsActions.UserSettingsDelay.INFREQUENT_USER_ACTION)
```

Este código no requiere cambios, conserva todas tus otras configuraciones de apariencia (como el tema), y automáticamente incluye todas las cabeceras relevantes de Discord, reduciendo al mínimo cualquier riesgo.

### ¿Cómo funciona esto?
Esto emula el cambio del interruptor 'Mostrar nuevo diseño' en la configuración de apariencia. Sí, por alguna razón, el interruptor está sincronizado con el servidor.

Nota: Esto es solo una solución temporal. Discord dejará de tener en cuenta esa configuración en alguna actualización futura.

### Última comprobación de funcionamiento: **22/12/2023**





### ¡Sígueme!
[![YouTube](https://img.shields.io/youtube/channel/subscribers/UCRrxALZwtn_D5VsSmnkDhAQ?style=for-the-badge)](https://youtube.com/tecnobros)
