# reactive-from-Angular
reactive FROM   Angular

<div>
    <form [formGroup]="student" novalidate (ngsubmit)="student.valid && onsubmit(student.value)">
        <p>
            <label>Username:</label>
            <input type="text" name="Name" required minlength="5" formControlName="Username" >
            <small style="color: red;" *ngIf="f['Username'].touched && f['Username'].hasError('required')"> Username
                required </small>
            <small style="color: red;" *ngIf="f['Username'].touched && f['Username'].hasError('minlength')"> Username
                type </small>
        </p>

        <p>
            <label>Mobile</label>
            <input type="text" name="Mobile" required minlength="9" formControlName="Mobile">
            <small style="color: red;" *ngIf="f['Mobile'].touched && f['Mobile'].hasError('required')"> Mobile required 
            </small>
            <small style="color: red;" *ngIf="f['Mobile'].touched && f['Mobile'].hasError('minlength')"> Mobile type 10
            </small>

        </p>



        <p>
            <label>Email</label>
            <input type="text" name="Name" required minlength="3" formControlName="Email">
            <small style="color: red;" *ngIf="f['Email'].touched && f['Email'].hasError('required')"> Email required
            </small>
            <small style="color: red;" *ngIf="f['Email'].touched && f['Email'].hasError('minlength')"> Email type
            </small>
        </p>



        <button type="submit" [disabled]="!student.valid">Sumit click!</button>




    </form>


</div>


export class ReactiveFormComponent {

student!:FormGroup;




constructor(private fb:FormBuilder){

}

  ngOnInit(): void {
    this.student=this.fb.group({
      Username:['',[Validators.required,Validators.minLength(5)]],
      Mobile:['',new FormControl()],
      Email:['',new FormControl()],

    })
  }
 public  get f(){
  return this.student.controls
}

  onsubmit(FormGroup: any) {
    console.log("formgroup",FormGroup);
    
    }
    
    

}

