# myFirstAndroidApp
package com.example.diceroller

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.TextView
import android.widget.Toast

/**
 * This activity allows the user to roll a dice and view the result
 * on the screen.
 */
class MainActivity : AppCompatActivity() {
    /**
     * onCreate is like the main in previous courses.
     */
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // Find the Button in the layout
        val rollButton: Button = findViewById(R.id.button)

        // Set a click listener on the button to roll the dice when the user taps the button
        rollButton.setOnClickListener {rollDice()}
        /**
         * These are older versions of what inside of rollButton.setOnClickListener{}
         * Version 1:
         * val toast = Toast.makeText(this, "Dice Rolled!", Toast.LENGTH_SHORT).show()
         * The line above demonstrates toast create a temporary message
         * Version 2:
         * val resultTextView: TextView = findViewById(R.id.textView)
         * resultTextView.text = "6"
         * The lines above demonstrate after clicking the button, the text 6 will show
         */


    }

    /**
     * Roll the dice and update the screen with the result.
     */
    private fun rollDice() {
        // Create new dice object with 6 sides and roll it
        val dice = Dice(6)
        val diceRoll = dice.roll()

        // Update the screen with the dice roll
        val resultTextView: TextView = findViewById(R.id.textView)
        resultTextView.text = diceRoll.toString()
    }
}

/**
 * Dice with a fixed number of sides.
 */
class Dice(private val numSides:Int){

    /**
     * Do a random dice roll and return the results.
     */
    fun roll(): Int{
        return (1..numSides).random()
    }
}
