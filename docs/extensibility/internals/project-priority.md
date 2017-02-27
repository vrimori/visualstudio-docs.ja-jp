---
title: "プロジェクトの優先順位 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクト [Visual Studio SDK] 項目を開く"
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# プロジェクトの優先順位
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プロジェクト項目はソリューションの 1 種類のプロジェクトのメンバーです。  したがって簡単に項目を開くとそのプロジェクトが使用されているかを調べることができます。  ただし項目が複数のプロジェクトのメンバーである場合項目を開くための最善のプロジェクトを決定優先度の設定を使用します。  
  
 次の一覧はプロジェクトの優先順位の設定を示しています :  
  
-   IDE でソリューション内の各プロジェクトの <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> のメソッドを文書がプロジェクトのメンバーかどうかを判断します。  
  
-   ドキュメントがプロジェクトのメンバーである場合プロジェクトはそのドキュメントの処理に割り当てた優先順位に従って応答します。  たとえば言語のプロジェクトでは言語のソース ファイル用の優先順位と応答しますがビルド処理の一部として使用されない認識されないファイルの種類の低い優先順位で応答します。  
  
-   文書にカスタムプロジェクト固有のエディターまたはデザイナーを提供するプロジェクトは優先順位が表示されます。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> の列挙はドキュメントの優先順位値を指定します。  
  
-   優先順位を指定するプロジェクトがドキュメントを開くコンテキストが与えられます。  2 つのプロジェクトが同じ優先順位値を返すとアクティブなプロジェクトが優先されます。  文書を開くことができるソリューションのプロジェクトが応答しない IDE でそのほかのファイル プロジェクトにドキュメントを配置します。  詳細については、「[その他のファイル プロジェクト](../../extensibility/internals/miscellaneous-files-project.md)」を参照してください。  
  
## 参照  
 [その他のファイル プロジェクト](../../extensibility/internals/miscellaneous-files-project.md)   
 [方法: 開いているドキュメントのエディターを開く](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [プロジェクトとプロジェクト項目テンプレートを追加します。](../../extensibility/internals/adding-project-and-project-item-templates.md)