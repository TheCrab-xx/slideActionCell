Slide Action Cell
===============

A UITableViewCell subclass that implements slide to action

##Usage

Import the SlideActionCell class. Inside your cellForRowAtIndexPath use the provided class methods to setup your cell.

```objc
-(UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath{
    NSString *cellIdentifier = @"Cell";
    [self.tableView registerClass:[SlideActionCell class] forCellReuseIdentifier:cellIdentifier];

    SlideActionCell *cell = [self.tableView dequeueReusableCellWithIdentifier:cellIdentifier forIndexPath:indexPath];
    if (!cell){
        cell = [[SlideActionCell alloc] initWithStyle:UITableViewCellStyleDefault reuseIdentifier:cellIdentifier];
    }

    [cell setText:self.tableData[indexPath.row]];

    if (indexPath.row == 2){

        [cell addLeftActionImage:[UIImage imageNamed:@"tick"]
                           color:[UIColor colorWithRed:0.157 green:0.761 blue:0.839 alpha:1]
                           width:80];

    }else{

        [cell addLeftAction:@"YES"
                      color:[UIColor colorWithRed:0.157 green:0.761 blue:0.839 alpha:1]
                  textColor:[UIColor whiteColor]
                      width:100];

    }

    [cell addRightAction:@"DELETE"
                   color:[UIColor colorWithRed:0.922 green:0.373 blue:0.286 alpha:1]
               textColor:[UIColor whiteColor]
                   width:100];

    [cell setDelegate:self];

    return cell;
}
```

##Delegate

The Delegate ( SlideActionCellDelegate ) has two required methods for when the left action is triggered and when the right action is triggered. Remember to set the delegate using setDelegate: inside cellForRowAtIndexPath

```objc
-(void)cellTriggeredLeftAction:(SlideActionCell *)cell;
-(void)cellTriggeredRightAction:(SlideActionCell *)cell;
```

##Note

I started this to teach myself the concept. If you run into any issues please log them here
https://github.com/Thomascullen92/slideActionCell/issues

## Licence

MIT 





