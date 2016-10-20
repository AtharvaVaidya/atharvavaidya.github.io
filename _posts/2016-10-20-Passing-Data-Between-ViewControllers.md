TLDR: Get a reference to the view controller you're going to segue to somehow and then do whatever you want.

## In prepareForSegue

{%highlight swift%}

override func prepare(for segue: UIStoryBoardSegue, sender: Any?)
{	
	let vc = segue.destination as! YourViewController
	vc.instanceVariable = someValue
}

{%endhighlight%}

## In a TableViewDelegate Method

{%highlight swift%}

override func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath)
{
	let segue = UIStoryboardSegue(identifier: "segueID", source: sourceVieController, destination: destinationViewController)
	let destination = segue.destination as! destinationViewController
	destination.instanceVariable = someValue
	segue.perform()
}

{%endhighlight%}




	

