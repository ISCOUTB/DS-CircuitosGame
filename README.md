using UnityEngine;
using UnityEngine.UI;

public class TerminalInteraction : MonoBehaviour
{
    public GameObject terminalUI; // UI de la terminal
    private bool isNearTerminal = false;

    void Start()
    {
        if (terminalUI != null)
            terminalUI.SetActive(false);
    }

    void Update()
    {
        if (isNearTerminal && Input.GetKeyDown(KeyCode.E))
        {
            ToggleTerminal();
        }
    }

    void ToggleTerminal()
    {
        if (terminalUI != null)
        {
            terminalUI.SetActive(!terminalUI.activeSelf);
        }
    }

    private void OnTriggerEnter(Collider other)
    {
        if (other.CompareTag("Player"))
        {
            isNearTerminal = true;
        }
    }

    private void OnTriggerExit(Collider other)
    {
        if (other.CompareTag("Player"))
        {
            isNearTerminal = false;
            if (terminalUI != null)
                terminalUI.SetActive(false);
        }
    }
}
