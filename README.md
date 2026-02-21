# CS50-PSET-2.1

#include <cs50.h>
#include <stdio.h>
#include <string.h>
#include <ctype.h>

// Prototype
int compute_da_score(string word);

int main(void)
{
    // Get words from both players
    string word1 = get_string("Player 1: ");
    string word2 = get_string("Player 2: ");

    // Compute scores
    int score1 = compute_da_score(word1);
    int score2 = compute_da_score(word2);

    // Compare and print result
    if (score1 > score2)
    {
        printf("Player 1 wins!\n");
    }
    else if (score2 > score1)
    {
        printf("Player 2 wins!\n");
    }
    else
    {
        printf("Tie!\n");
    }
}

// Computes the Scrabble score for a word
int compute_da_score(string word)
{
    // Point values for A–Z
    int POINTS[] = {1, 3, 3, 2, 1, 4, 2, 4, 1, 8, 5, 1, 3, 1, 1, 3, 10, 1, 1, 1, 1, 4, 4, 8, 4, 10};

    int score = 0;

    // Loop through each character in the word
    for (int i = 0, n = strlen(word); i < n; i++)
    {
        if (isalpha(word[i]))
        {
            char c = toupper(word[i]);
            score += POINTS[c - 'A'];
        }
    }

    return score;
}
