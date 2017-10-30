# UITableView
* 注意Table view cell的style，默认是basic，如果是自己定义的类，要选custom
* 如果没有跳转，查看navigationController 是否初始化了，在edit->embed in->navigation controller设置，把元素包进去
* 在外层不能直接访问下层的类，因为此时子类还没创建好，正确的做法是可以传参数进去：这里不能直接设置vc.label.text, 而是在vc中暴露一个labelText字段，用来在外面设置，然后在vc内部赋值

```swift
    override func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        if let vc = storyboard?.instantiateViewController(withIdentifier: "DetailViewController") as? DetailViewController {
            vc.labelText = pictures[indexPath.row]
            self.navigationController?.pushViewController(vc, animated: true)
        }
    }
```
