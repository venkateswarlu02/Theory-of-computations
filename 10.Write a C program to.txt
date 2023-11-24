#include <stdio.h>
#include <stdbool.h>
#define MAX_STATES 100
#define MAX_TRANSITIONS 100
typedef struct {
    int state;
    int transition;
} Transition;
typedef struct {
    int numStates;
    int numTransitions;
    Transition transitions[MAX_TRANSITIONS];
} NFA;
void epsilonClosure(NFA nfa, int state, bool visited[], bool closure[]) {
    visited[state] = true;
    closure[state] = true;

    for (int i = 0; i < nfa.numTransitions; i++) {
        Transition transition = nfa.transitions[i];
        if (transition.state == state && transition.transition == -1) {
            int nextState = nfa.transitions[i].transition;
            if (!visited[nextState]) {
                epsilonClosure(nfa, nextState, visited, closure);
            }
        }
    }
}
int main() {
    NFA nfa;
    printf("Enter the number of states: ");
    scanf("%d", &nfa.numStates);
    printf("Enter the number of transitions: ");
    scanf("%d", &nfa.numTransitions);
    printf("Enter transition information:\n");
    for (int i = 0; i < nfa.numTransitions; i++) {
        printf("Transition %d: (state, transition) = ", i + 1);
        scanf("%d%d", &nfa.transitions[i].state, &nfa.transitions[i].transition);
    }
    printf("\ne-Closure for each state:\n");
    for (int i = 0; i < nfa.numStates; i++) {
        bool visited[MAX_STATES] = {false};
        bool closure[MAX_STATES] = {false};
        epsilonClosure(nfa, i, visited, closure);
        printf("e-Closure(q%d): { ", i);
        for (int j = 0; j < nfa.numStates; j++) {
            if (closure[j]) {
                printf("q%d ", j);
            }
        }
        printf("}\n");
    }
    return 0;
}
