# Avance

import QtQuick 2.6
import QtQuick.Window 2.2
import QtQuick.Controls 1.4
import QtQuick.Dialogs 1.2
import QtQuick 2.0
import QtQuick.Controls 1.2
import QtQuick.Dialogs 1.2


StackView
{
    id: root
    height: 500
    width: 300
    initialItem: inicio

    Component
    {
        id: inicio
        Rectangle
        {
            color: "#4A4A4A"

            Text
            {
                id: bienvenido
                text: "Bienvenido"
                x: 78
                y: 65
                font.pixelSize: 30
                color: "darkgreen"
                style: Text.Sunken
                styleColor: "black"
            }

            Text
            {
                id: lineatext
                text: "-----------------------------------------"
                color: "white"
                x: 75
                y: 105
                font.pixelSize: 10
            }

            Text
            {
                id: incuentatext
                text: "Ingrese con su cuenta"
                color: "white"
                x: 109
                y: 120
                font.pixelSize: 10
            }

            Rectangle
            {
                id: r2
                height: 30
                width: 120
                x: 125
                y: 150
                color: "lightgray"
                border.color: "gray"
                border.width: 3
                radius: 10

                TextInput
                {
                    id: usuario
                    anchors.fill: parent
                    anchors.margins: 10
                    KeyNavigation.tab: contraseña
                    focus: true
                }
            }

            Text
            {
                id: usuariotext
                text: "Usuario:"
                color: "white"
                x: 60
                y: 155
                font.pixelSize: 15
            }

            Rectangle
            {
                id: r3
                height: 30
                width: 120
                x: 125
                y: 200
                color: "lightgray"
                border.color: "gray"
                border.width: 3
                radius: 10

                TextInput
                {
                    id: contraseña
                    anchors.fill: parent
                    anchors.margins: 10
                    echoMode: TextInput.Password
                    KeyNavigation.tab: usuario
                }
            }

            Text
            {
                id: contraseñatext
                text: "Contraseña:"
                color: "white"
                x: 40
                y: 205
                font.pixelSize: 15
            }

            Rectangle
            {
                id: r4
                height: 50
                width: 180
                x: 67
                y: 250
                color: "lightgreen"
                border.color: "green"
                border.width: 3
                radius: 10

                Text
                {
                    id: insesiontext
                    anchors.centerIn: parent
                    text: "INICIAR SESIÓN"
                }

                signal send()
                onSend: console.log("Usuario: " + usuario.text + " Contraseña: " + contraseña.text)

                MouseArea
                {
                    id: logging
                    anchors.fill: parent
                    onClicked:  root.push(niuventana)

                }

                Component.onCompleted:
                {
                    logging.clicked.connect(send)
                }

            }

        }
    }

    Component
    {
        id: niuventana

        Rectangle
        {
            id: niu
            width: 300
            height: 500
            color: "black"

            Text
            {
                id: blah
                color: "white"
                anchors.centerIn: parent
                text: qsTr("Nueva ventana.")
            }

            MouseArea
            {
                anchors.fill: parent
                onClicked: root.push(inicio)
            }
        }
    }
}
