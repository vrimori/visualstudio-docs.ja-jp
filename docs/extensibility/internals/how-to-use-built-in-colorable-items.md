---
title: '方法: 組み込みの配色可能な項目を使用して、|Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f0900792b92a185ce7da66440e0b368870e97be
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965956"
---
# <a name="how-to-use-built-in-colorable-items"></a>方法: 組み込みの配色可能な項目を使用して、
組み込みの配色可能な項目を使用する前にする必要があります最初に通知する、統合開発環境 (IDE) ここで可能性のあるカスタム独自配色可能な項目を提供していない<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>オブジェクト。 言語サービスのレジストリ エントリを設定して行います。  
  
## <a name="to-use-built-in-colorable-items"></a>組み込みの配色可能な項目を使用するには  
  
1. **HKEY_LOCAL_MACHINE\VisualStudio\\< X.Y > \Languages\Language サービス\\< 言語名\>** ここで、 \<X.Y > のバージョンは、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]と\<言語名 > 名前を指定します、言語の作成という DWORD レジストリ エントリ値**RequestStockColors**します。  
  
2. 設定、 **RequestStockColors**レジストリ エントリの値を*1*します。  
  
    レジストリ エントリを colorizer を作成した後<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A>メソッドのメンバーが使用できる、<xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS>エディターによって使用される色の属性の配列を埋めるために列挙します。  
  
   > [!NOTE]
   >  カスタムの配色可能な項目を指定する場合は、このレジストリ エントリを設定しないでください。 詳細については、次を参照してください。[カスタム装飾が可能なアイテム](../../extensibility/internals/custom-colorable-items.md)します。  
  
## <a name="see-also"></a>関連項目  
 [構文のカスタム エディターで色分け表示](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [構文の色分け、従来の言語サービス](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [構文の色分けを実装します。](../../extensibility/internals/implementing-syntax-coloring.md)   
 [カスタムの配色可能な項目](../../extensibility/internals/custom-colorable-items.md)   
 [従来の言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service2.md)