<script setup>
import { Calendar } from '@awesome-cordova-plugins/calendar'

const startDate = new Date()
const endDate = new Date(startDate.getTime() + 30 * 24 * 60 * 60 * 1000)

Calendar.requestReadPermission()
    .then(() => {})
    .catch((error) => {
        console.log('Error requesting permission', error)
    })

function createEvent() {
    Calendar.createEvent(
        'Awesome Cordova Plugin',
        'Awesome Cordova Plugin',
        'Awesome Cordova Plugin',
        startDate,
        endDate
    )
        .then(() => {
            console.log('Event created successfully')
        })
        .catch((error) => {
            console.log('Error creating event', error)
        })
}

function logEvents() {
    try {
        Calendar.findEvent('', '', '', startDate, endDate).then((events) =>
            console.log('events: ', events)
        )
    } catch (e) {
        console.error('error', e)
    }
}
</script>

<template>
    <h1>Hello World</h1>

    <button @click="createEvent">Create Event</button>
    <button @click="logEvents">Log Events Event</button>
</template>

<style></style>
