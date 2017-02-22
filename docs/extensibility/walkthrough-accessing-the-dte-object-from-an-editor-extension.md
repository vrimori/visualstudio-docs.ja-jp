---
title: "チュートリアル: エディター拡張機能から DTE オブジェクトにアクセスします。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] 新しい - DTE オブジェクトを取得します。"
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# チュートリアル: エディター拡張機能から DTE オブジェクトにアクセスします。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vspackages にあるを呼び出して、DTE オブジェクトを取得できる、 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> DTE オブジェクトの型を持つメソッドです。 Managed Extensibility Framework \(MEF\) 拡張機能でインポートできる <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> しを呼び出す、 <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> の型を持つメソッド <xref:EnvDTE.DTE>します。  
  
## 必須コンポーネント  
 このチュートリアルを行うには、Visual Studio SDK をインストールする必要があります。 詳細については、「[Visual Studio SDK](../extensibility/visual-studio-sdk.md)」を参照してください。  
  
## DTE オブジェクトを取得します。  
  
#### DTE オブジェクトをサービス プロバイダーから取得するには  
  
1.  という名前の C\# の場合は、VSIX プロジェクトを作成する `DTETest`です。 エディターの分類子の項目テンプレートを追加し、名前 `DTETest`します。 詳細については、「[エディター項目テンプレートを使用して拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)」を参照してください。  
  
2.  プロジェクトには、次のアセンブリ参照を追加します。  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3.  DTETest.cs ファイルを開き、次の追加 `using` ディレクティブ。  
  
    ```c#  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4.  `GetDTEProvider` クラスで、インポート、 <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>です。  
  
    ```c#  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5.  `GetClassifier()` メソッドに次のコードを追加します。  
  
    ```c#  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6.  使用する必要がある場合、 <xref:EnvDTE80.DTE2> インターフェイス、して DTE オブジェクトをキャストすることができます。  
  
## 参照  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)