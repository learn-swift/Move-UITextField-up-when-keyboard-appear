## Move UITextField up when keyboard appears in Swift

```Swift
@IBOutlet weak var emailTextField		: UITextField!

override func viewDidLoad() {
		super.viewDidLoad()
		emailTextField.delegate = self
	}	

func textFieldDidBeginEditing(textField: UITextField) {
		animateViewMoving(true, moveValue: 200)
	}
	func textFieldDidEndEditing(textField: UITextField) {
		animateViewMoving(false, moveValue: 200)
	}

	func animateViewMoving (up:Bool, moveValue :CGFloat){
		let movementDuration:NSTimeInterval = 0.3
		let movement:CGFloat = ( up ? -moveValue : moveValue)
		UIView.beginAnimations( "animateView", context: nil)
		UIView.setAnimationBeginsFromCurrentState(true)
		UIView.setAnimationDuration(movementDuration )
		self.view.frame = CGRectOffset(self.view.frame, 0,  movement)
		UIView.commitAnimations()
	}
```	
