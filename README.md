using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class PlayerController2 : MonoBehaviour
{
    public float speed = 0.05f;
    private Animator animator;

    void Start()
    {
        animator = GetComponent<Animator>();
    }
    void Update(){
        if(Input.GetAxisRaw("Horizontal") < 0 || Input.GetAxisRaw("Horizontal") > 0){
            transform.Translate(Input.GetAxisRaw("Horizontal") * speed , 0, 0);
            transform.localScale = new Vector2(Input.GetAxisRaw("Horizontal"), 1); 
            animator.SetBool("RunStart", true);
        } else if(Input.GetAxisRaw("Horizontal") == 0) {
            animator.SetBool("RunStart", false); 
        } 
        if (Input.GetAxisRaw("Vertical") > 0 || Input.GetKey(KeyCode.Space)) { 
            // Debug.Log("상하: " + Input.GetAxisRaw("Vertical"));
            transform.Translate(0, speed, 0);
            animator.SetBool("JumpStart", true);
        }  else {
            animator.SetBool("JumpStart", false); 
        }
    }
}
