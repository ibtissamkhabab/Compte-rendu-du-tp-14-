package TP14

import kotlinx.coroutines.*

fun main() = runBlocking {
    println("Début du programme")

    val jobGlobal = GlobalScope.launch {
        delay(2000)
        println("GlobalScope : tâche terminée")
    }

    val scope = CoroutineScope(Dispatchers.Default)
    val jobCustom = scope.launch {
        delay(3000)
        println("CoroutineScope : tâche terminée")
    }

    launch {
        delay(1000)
        println("runBlocking : tâche terminée")
    }

    delay(1500)
    jobGlobal.cancel()
    println("GlobalScope annulée")

    jobCustom.join()
    println("Fin du programme")
}


