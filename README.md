using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class PlayerController : MonoBehaviour
{
    private Animator animator;
    private Rigidbody2D playerRigidbody;
    public float speed = 10f;
    public Vector2 position;

    void Start()
    {
        animator = GetComponent<Animator>();
        playerRigidbody = GetComponent<Rigidbody2D>();
        position = transform.position;
    }

    void Update()
    {
        if(Input.GetMouseButtonDown(0)){
            Debug.Log("마우스 왼쪽 버튼");
        }
        if(Input.GetMouseButtonDown(1)){
            Debug.Log("마우스 오른쪽 버튼");
        }
        if(Input.GetKeyDown(KeyCode.Space)){
            Debug.Log("스페이스바");
        }
        if(Input.GetKeyDown(KeyCode.LeftArrow) || Input.GetKeyDown(KeyCode.A)){
            transform.localScale = new Vector2(-1, 1);  
        }
        if(Input.GetKeyDown(KeyCode.RightArrow) || Input.GetKeyDown(KeyCode.D)){
            transform.localScale = new Vector2(1, 1);  
        }
        if(Input.GetKeyUp(KeyCode.LeftArrow) || Input.GetKeyUp(KeyCode.RightArrow) || Input.GetKeyUp(KeyCode.UpArrow) || Input.GetKeyUp(KeyCode.DownArrow)){
            animator.SetBool("RunStart", false); 
        }
        if(Input.GetKeyUp(KeyCode.A) || Input.GetKeyUp(KeyCode.S) || Input.GetKeyUp(KeyCode.W) || Input.GetKeyUp(KeyCode.D)){
            animator.SetBool("RunStart", false); 
        }
        // 왼쪽, 오른쪽으로 움직이기
        if (Input.GetAxisRaw("Horizontal") > 0 || Input.GetAxisRaw("Horizontal") < 0) { 
            Debug.Log("좌우");
            animator.SetBool("RunStart", true);
            transform.Translate(new Vector2(Input.GetAxisRaw("Horizontal") * speed * Time.deltaTime, 0f));
        } 
        // 위, 아래로 움직이기
        if (Input.GetAxisRaw("Vertical") > 0 || Input.GetAxisRaw("Vertical") < 0) { 
            Debug.Log("상하");
            animator.SetBool("RunStart", true);
            transform.Translate(new Vector2(0f, Input.GetAxisRaw("Vertical") * speed * Time.deltaTime));
        } 
    }
}
