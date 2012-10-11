PaperTrail
==========

PaperTrail iOS App

UIImagePickerController *imagePicker =
    [[UIImagePickerController alloc] init];
    
    // If our device has a camera, we want to take a picture, otherwise, we
    // just pick from photo library
    if ([UIImagePickerController
         isSourceTypeAvailable:UIImagePickerControllerSourceTypeCamera]) {
        [imagePicker setSourceType:UIImagePickerControllerSourceTypeCamera];
    } else {
        [imagePicker setSourceType:UIImagePickerControllerSourceTypePhotoLibrary];
    }
    
    [imagePicker setDelegate:self];
    
    // Place image picker on the screen
    if ([[UIDevice currentDevice] userInterfaceIdiom] == UIUserInterfaceIdiomPhone) {
        // Create a new popover controller that will display the imagePicker
        imagePickerPopover = [[UIPopoverController alloc] 
                              initWithContentViewController:imagePicker];
        
        [imagePickerPopover setDelegate:self];
        
        // Display the popover controller, sender 
        // is the camera bar button item
        [imagePickerPopover presentPopoverFromBarButtonItem:sender
                                   permittedArrowDirections:UIPopoverArrowDirectionAny
                                                   animated:YES];
    } else {
        [self presentViewController:imagePicker animated:YES completion:nil];
    }
