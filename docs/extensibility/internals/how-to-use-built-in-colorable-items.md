---
title: "方法: ビルトインの装飾が可能な項目を使用して | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "装飾が可能な項目"
  - "言語サービスでは、組み込みの装飾が可能な項目"
ms.assetid: 5e5f3436-6bad-4fd2-8823-6a30353ba648
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 方法: ビルトインの装飾が可能な項目を使用して
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

組み込みの色設定可能項目を使用する前にこの場合 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> の \(IDE\) オブジェクトである独自のカスタム色設定可能項目を指定しないと統合開発環境に通知を送信する必要があります。  言語サービスのレジストリ エントリを設定する必要があります。  
  
### 組み込みの色設定可能項目を指定する  
  
1.  HKEY\_LOCAL\_MACHINE \\ VisualStudio \\*X.Y*\\ *X.Y* が [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のバージョンである  *言語名*  が言語の名前である言語 \\ Services \\ *言語名*  言語でダブル ワードのレジストリ エントリの値によって呼び出される `RequestStockColors` を作成します。  
  
2.  1. に `RequestStockColors` のレジストリ エントリの値を設定します。  
  
     レジストリ エントリを作成したらcolorizer の <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> のメソッドはエディターに使用する属性の色の配列を設定するに <xref:Microsoft.VisualStudio.TextManager.Interop.DEFAULTITEMS> の列挙体のメンバーを使用します。  
  
    > [!NOTE]
    >  カスタム色設定可能項目を使用してこのレジストリ エントリを設定しないでください。  詳細については、「[カスタムの装飾が可能な項目](../../extensibility/internals/custom-colorable-items.md)」を参照してください。  
  
## 参照  
 [構文のカスタム エディターの色指定](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [構文の色分けで従来の言語サービス](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [構文の色分けを実装します。](../../extensibility/internals/implementing-syntax-coloring.md)   
 [カスタムの装飾が可能な項目](../../extensibility/internals/custom-colorable-items.md)   
 [従来の言語サービスを登録します。](../../extensibility/internals/registering-a-legacy-language-service2.md)