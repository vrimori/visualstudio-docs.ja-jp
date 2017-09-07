---
title: "ストアのビューアーを使用してデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 17
author: alancameronwills
ms.author: awills
manager: douge
ms.translationtype: MT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 6fde5dfc012b43d71f6d8db2519607724eeeadc9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

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
  
## <a name="see-also"></a>関連項目  
 [プログラム コードにおけるモデル内の移動およびモデルの更新](../modeling/navigating-and-updating-a-model-in-program-code.md)
