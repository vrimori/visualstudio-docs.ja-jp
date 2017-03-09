---
title: "IVsPackage インターフェイスの実装 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IVsPackage インターフェイス"
  - "インターフェイス、IVsPackage の実装"
ms.assetid: 0c76b2e1-ce63-47fc-93ee-847cad281fc1
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# IVsPackage インターフェイスの実装
すべての VSPackages は <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> のインターフェイスを実装する必要があります。  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] は関連付けられたプロパティ ページを取得するために初期化VSPackage を閉じるように <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> のメソッドを他の理由で呼び出します。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> のインターフェイスは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] と VSPackage 間のためのインターフェイスです。  
  
 目的の <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> を実行する <xref:Microsoft.VisualStudio.Shell.Package> クラスのサブクラスとしてマネージ VSPackage を作成できます。  詳細については、「[マネージ VSPackage](../misc/managed-vspackages.md)」を参照してください。  
  
> [!NOTE]
>  [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Visual Studio の統合のセクションのアンマネージ コード例の多くは Active Template Library を使用します \(ATL\)。  VSPackage を作成するにはATL を使用する必要はありませんサンプル コードを理解するためにATL を理解する必要があります。  
  
## 参照  
 [Vspackages にあります。](../extensibility/internals/vspackages.md)