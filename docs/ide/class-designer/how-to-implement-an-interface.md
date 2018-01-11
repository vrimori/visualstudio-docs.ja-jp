---
title: "方法: インターフェイスを実装する (クラス デザイナー) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c926da09cb8bbb191d0d307dd9e8ce16cfef3c20
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-an-interface-class-designer"></a>方法: インターフェイスを実装する (クラス デザイナー)
クラス デザイナーのクラス ダイアグラム上で、インターフェイス メソッド用のコードを提供するクラスに接続して、インターフェイスを実装できます。 クラス デザイナーによってインターフェイス実装が生成され、インターフェイスとクラス間の関係が継承関係として表示されます。 インターフェイスとクラスの間に継承線を描画するか、インターフェイスをクラス ビューからドラッグすることにより、インターフェイスを実装できます。  
  
> [!TIP]
>  インターフェイスは、他の型を作成するのと同じ方法で作成できます。 インターフェイスが存在していてもクラス ダイアグラムに表示されていない場合は、最初にインターフェイスを表示します。 詳しくは、「[方法: クラス デザイナーを使用して型を作成する](how-to-create-types.md)」および「[方法: 既存の型を表示する](how-to-view-existing-types.md)」をご覧ください。  
  
### <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>継承線を描画してインターフェイスを実装するには  
  
1.  クラス ダイアグラムで、インターフェイスおよびインターフェイスを実装するクラスを表示します。  
  
2.  クラスとインターフェイスから継承線を描画します。  
  
     クラスにアタッチされたロリポップが表示され、インターフェイス名が表示されたラベルによって継承関係が示されます。 Visual Studio は、すべてのインターフェイス メンバーのスタブを生成します。  
  
 詳しくは、「[方法: 型の間の継承を作成する](how-to-create-inheritance-between-types.md)」をご覧ください。  
  
### <a name="to-implement-an-interface-from-the-class-view-window"></a>[クラス ビュー] ウィンドウからインターフェイスを実装するには  
  
1.  クラス ダイアグラムで、インターフェイスを実装するクラスを表示します。  
  
2.  クラス ビューを開き、インターフェイスを探します。  
  
    > [!TIP]
    >  クラス ビューが開いていない場合は、**[表示]** メニューから開きます。 クラス ビューの詳細については、「[クラスとそのメンバーを表示する](http://msdn.microsoft.com/en-us/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333)」を参照してください。  
  
3.  インターフェイス ノードをダイアグラムのクラスの図形にドラッグします。  
  
     クラスにアタッチされたロリポップが表示され、インターフェイス名が表示されたラベルによって継承関係が示されます。 Visual Studio は、すべてのインターフェイス メンバーのスタブを生成します。この時点で、インターフェイスが実装されます。  
  
## <a name="see-also"></a>関連項目
[方法: クラス デザイナーを使用して型を作成する](how-to-create-types.md)   
[方法: 既存の型を表示する](how-to-view-existing-types.md)   
[方法: 型の間の継承を作成する](how-to-create-inheritance-between-types.md)   
[クラスおよび型のリファクタリング](refactoring-classes-and-types.md)