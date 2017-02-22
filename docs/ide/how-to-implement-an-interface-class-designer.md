---
title: "How to: Implement an Interface (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interfaces [Visual Studio], implementing"
  - "interfaces [Visual Studio]"
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Implement an Interface (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

クラス デザイナーでは、インターフェイスのメソッドのコードを提供するクラスにインターフェイスを接続することにより、クラス ダイアグラムにインターフェイスを実装できます。  クラス デザイナーによってインターフェイス実装が生成され、インターフェイスとクラス間の関係が継承関係として表示されます。  インターフェイスとクラスの間に継承線を描画するか、インターフェイスをクラス ビューからドラッグすることにより、インターフェイスを実装できます。  
  
> [!TIP]
>  他の型を作成するのと同じ方法で、インターフェイスも作成できます。  インターフェイスが存在していてもクラス ダイアグラムに表示されていない場合は、最初にインターフェイスを表示します。  詳細については、「[How to: Create Types by using Class Designer](../ide/how-to-create-types-by-using-class-designer.md)」および「[How to: View Existing Types \(Class Designer\)](../Topic/How%20to:%20View%20Existing%20Types%20\(Class%20Designer\).md)」を参照してください。  
  
### 継承線を描画してインターフェイスを実装するには  
  
1.  クラス ダイアグラムで、インターフェイスおよびインターフェイスを実装するクラスを表示します。  
  
2.  クラスとインターフェイスから継承線を描画します。  
  
     クラスに追加されたロリポップが表示され、インターフェイス名が表示されたラベルによって継承関係が示されます。  Visual Studio は、すべてのインターフェイス メンバーのスタブを生成します。  
  
 詳細については、「[How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md)」を参照してください。  
  
### \[クラス ビュー\] ウィンドウからインターフェイスを実装するには  
  
1.  クラス ダイアグラムで、インターフェイスを実装するクラスを表示します。  
  
2.  クラス ビューを開き、インターフェイスを探します。  
  
    > [!TIP]
    >  クラス ビューが開いていない場合は、**\[表示\]** メニューから開きます。  クラス ビューの詳細については、「[Viewing Classes and Their Members](http://msdn.microsoft.com/ja-jp/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333)」を参照してください。  
  
3.  インターフェイス ノードをダイアグラムのクラスの図形にドラッグします。  
  
     クラスに追加されたロリポップが表示され、インターフェイス名が表示されたラベルによって継承関係が示されます。  Visual Studio は、すべてのインターフェイス メンバーのスタブを生成します。この時点で、インターフェイスが実装されます。  
  
## 参照  
 [How to: Create Types by using Class Designer](../ide/how-to-create-types-by-using-class-designer.md)   
 [How to: View Existing Types \(Class Designer\)](../Topic/How%20to:%20View%20Existing%20Types%20\(Class%20Designer\).md)   
 [How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Refactoring Classes and Types \(Class Designer\)](../ide/refactoring-classes-and-types-class-designer.md)