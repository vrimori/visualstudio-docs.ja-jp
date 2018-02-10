---
title: "ストアのビューアーを使用してデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0d5d0b071014b5ec878b7d30b27b8cc07976d329
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="debugging-by-using-the-store-viewer"></a>ストア ビューアーを使用したデバッグ
ビューアーを使用して、格納の状態を調べることができます、*格納*によって使用される[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]です。 格納ビューアーでは、すべての要素のプロパティと要素間のリンクと共に、特定のストア内にあるドメイン モデル要素が表示されます。  
  
## <a name="opening-store-viewer"></a>開くストア ビューアー  
 起動したら、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]実験的なビルドは、ブレークポイントでコードを停止するには、ストアのインスタンスにモデルの情報が含まれています。 を開き、ストア ビューアーに次のコマンドを入力して、**イミディ エイト**ウィンドウ。  
  
```  
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);  
```  
  
> [!NOTE]
>  置き換える必要があります`mystore`ストアのインスタンスの名前に置き換えます。 また、コードに、名前空間を追加する場合は、完全修飾名前空間なしストア ビューアーを表示するコマンドを入力できます。  
>   
>  `using Microsoft.VisualStudio.Modeling.Diagnostics;`  
>   
>  `...`  
>   
>  `StoreViewer.Show(mystore);`  
  
 `Show`メソッドいくつかのオーバー ロードがあります。 ストアまたはパーティションのインスタンスは、パラメーターとして指定できます。  
  
 代わりに、コードで任意の場所、ストアのビューアーを表示するコードの行を配置することができますをパラメーターに渡す、`Show`メソッドがスコープ内にします。 このアクションは、コードの行をストアの内容のスナップショットとして実行するときに、格納のビューアーを表示します。  
  
### <a name="using-store-viewer"></a>ストアのビューアーを使用します。  
 ストア ビューアーが開き、Windows フォームされるモードレス ウィンドウが表示されます、として、次の図に示します。  
  
 ![](../modeling/media/storeviewer2.png "storeviewer2")  
ストア ビューアー  
  
 ストアのビューアーが 3 つのペイン: 左側のペイン、右上のペイン、および右下のペインです。 左側のウィンドウは、ツリー ビュー内の型の`DomainDataDirectory`ストアのメンバーです。 パーティションのノードを展開して要素をクリックすると、右上のペインで、要素のプロパティが表示されます。 要素が他の要素にリンクされている場合は、右下のペインに追加の要素が表示されます。 右下のペイン内の要素をダブルクリックすると、左側のウィンドウで、要素が強調表示されます。  
  
## <a name="see-also"></a>参照  
 [プログラム コードにおけるモデル内の移動およびモデルの更新](../modeling/navigating-and-updating-a-model-in-program-code.md)