---
title: 名前空間内の XML に対するクエリを記述する方法 (C#)
description: 名前空間内の XML に対するクエリを記述する方法について説明します。 これらのクエリでは、正しい名前空間を持つ XName オブジェクトを使用する必要があります。
ms.date: 07/20/2015
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: 64eb9df1cde3b434a11e2e5410aab96993dc0fa1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303180"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-c"></a>名前空間内の XML に対するクエリを記述する方法 (C#)
名前空間内の XML に対するクエリを記述するには、正しい名前空間を持つ <xref:System.Xml.Linq.XName> オブジェクトを使用する必要があります。  
  
 C# での最も一般的な方法は、URI を含んだ文字列を使用して <xref:System.Xml.Linq.XNamespace> を初期化し、加算演算子オーバーロードを使用して名前空間をローカル名に連結することです。  
  
 このトピックの最初に示す一連の例では、既定の名前空間内に XML ツリーを作成する方法を示します。 2 つ目の例では、プレフィックスを持つ名前空間で XML ツリーを作成する方法を示します。  
  
## <a name="example"></a>例  
 次の例では、既定の名前空間に含まれる XML ツリーを作成しています。 さらに、要素のコレクションを取得しています。  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```output  
1  
2  
3  
```  
  
## <a name="example"></a>例  
 C# では、プレフィックスを持つ名前空間を使用する XML ツリーでも、既定の名前空間を持つ XML ツリーでも、クエリを記述する方法は同じです。  
  
 次の例では、プレフィックスを持つ名前空間に含まれる XML ツリーを作成しています。 さらに、要素のコレクションを取得しています。  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = XElement.Parse(  
@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
    <aw:Child>1</aw:Child>  
    <aw:Child>2</aw:Child>  
    <aw:Child>3</aw:Child>  
    <aw:AnotherChild>4</aw:AnotherChild>  
    <aw:AnotherChild>5</aw:AnotherChild>  
    <aw:AnotherChild>6</aw:AnotherChild>  
</aw:Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```output  
1  
2  
3  
```  
  
## <a name="see-also"></a>関連項目

- [名前空間の概要 (LINQ to XML)](namespaces-overview-linq-to-xml.md)
