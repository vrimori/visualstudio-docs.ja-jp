---
title: '方法: ビルトインの配色可能な項目を使用して、|Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, built-in colorable items
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b537c28f34faff1eff0502642236413f2ade2da1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942167"
---
# <a name="how-to-use-built-in-colorable-items"></a>方法: ビルトインの配色可能な項目を使用して、
組み込みの配色可能な項目を使用する前にする必要があります最初に通知する、統合開発環境 (IDE) ここで可能性のあるカスタム独自配色可能な項目を提供していない<xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>オブジェクト。 言語サービスのレジストリ エントリを設定して行います。  
  
## <a name="to-use-built-in-colorable-items"></a>組み込みの配色可能な項目を使用するには  
  
1. **HKEY_LOCAL_MACHINE\VisualStudio\\< X.Y > \Languages\Language サービス\\< 言語名\>**、 \<X.Y > のバージョンが[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]と\<言語名 > は、名前と呼ばれる、レジストリ エントリの DWORD 値を作成、使用する言語の**RequestStockColors**。  
  
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