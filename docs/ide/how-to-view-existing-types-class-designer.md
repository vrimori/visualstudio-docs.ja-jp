---
title: "方法: 既存の型を表示する (クラス デザイナー) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 072962f0b699ad88cca8d3d0f10fa7fced926d3e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-view-existing-types-class-designer"></a>方法: 既存の型を表示する (クラス デザイナー)
既存の型とそのメンバーを表示するには、その図形をクラス ダイアグラムに追加します。  
  
 ローカル型と参照型を表示できます。 ローカル型は現在開いているプロジェクトに含まれ、読み取りと書き込みができます。 参照型は別のプロジェクトまたは参照アセンブリに含まれ、読み取り専用です。  
  
 クラス ダイアグラムで新しい型を設計する場合は、「[方法: クラス デザイナーを使用して型を作成する](../ide/how-to-create-types-by-using-class-designer.md)」を参照してください。  
  
### <a name="to-see-types-in-a-project-on-a-class-diagram"></a>プロジェクトの型をクラス ダイアグラムで表示するには  
  
1.  ソリューション エクスプローラーのプロジェクトから、既存のクラス ダイアグラム (.cd) ファイルを開きます。 クラス ダイアグラムが存在しない場合は、プロジェクトに新しいクラス ダイアグラムを追加します。 「[方法: プロジェクトにクラス ダイアグラムを追加する (クラス デザイナー)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)」を参照してください。  
  
2.  ソリューション エクスプローラーのプロジェクトから、ソース コード ファイルをクラス ダイアグラムにドラッグします。  
  
    > [!WARNING]
    >  ソリューションに複数のアプリでコードを共有しているプロジェクトがある場合、次のソースからのみファイルまたはコードをクラス ダイアグラムにドラッグできます。  
    >   
    >  -   ダイアグラムを含むアプリ プロジェクト  
    > -   アプリ プロジェクトによりインポートされた共有プロジェクト  
    > -   参照プロジェクト  
    > -   アセンブリ  
  
     ソース コード ファイルで定義された型を表す図形が、クラス ダイアグラムのファイルをドラッグした場所に表示されます。  
  
 クラス ビューのプロジェクト ノードから 1 つ以上の型をクラス ダイアグラムにドラッグしてプロジェクトの型を表示することもできます。  
  
> [!TIP]
>  クラス ビューが開いていない場合は、**[表示]** メニューから開きます。 クラス ビューの詳細については、「[クラスとそのメンバーを表示する](http://msdn.microsoft.com/en-us/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333)」を参照してください。  
  
 ダイアグラムの既定の場所で型を表示するには、クラス ビューで 1 つ以上の型を選択し、選択した型を右クリックし、**[クラス ダイアグラムで表示]** を選択します。  
  
> [!NOTE]
>  型を含む閉じられたクラス ダイアグラムが既にプロジェクトに存在する場合は、クラス ダイアグラムが開いて型シェイプが表示されます。 ただし、型を含むクラス ダイアグラムがプロジェクトに存在しない場合は、クラス デザイナーによって新しいクラス ダイアグラムがプロジェクトに作成されて開かれ、型が表示されます。  
  
 最初にダイアグラムで型を表示すると、図形は既定で縮小表示されます。 図形を展開して内容を表示できます。  
  
### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>クラス ダイアグラムで、プロジェクトの内容を表示するには  
  
1.  ソリューション エクスプローラーまたはクラス ビューで、プロジェクトを右クリックし、**[表示]** を選択してから **[クラス ダイアグラムの表示]** を選択します。  
  
     自動設定されたクラス ダイアグラムが作成されます。  
  
## <a name="see-also"></a>関連項目  
 [方法: 型の間の継承を表示する (クラス デザイナー)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [方法: クラス ダイアグラムをカスタマイズする (クラス デザイナー)](../ide/how-to-customize-class-diagrams-class-designer.md)   
 [型およびリレーションシップの表示 (クラス デザイナー)](../ide/viewing-types-and-relationships-class-designer.md)