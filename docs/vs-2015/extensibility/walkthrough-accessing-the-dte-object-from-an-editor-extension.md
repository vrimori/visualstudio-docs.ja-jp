---
title: 'チュートリアル: エディター拡張機能から DTE オブジェクトにアクセスする |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2669571fee0ea9f43c06ba9ec7526d0716931fe0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49239929"
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>チュートリアル: エディターの拡張機能から DTE オブジェクトにアクセスする
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vspackage では、呼び出すことによって、DTE オブジェクトを取得できます、 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> DTE オブジェクトの型を持つメソッド。 Managed Extensibility Framework (MEF) 拡張機能でインポートできる<xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>を呼び出して、<xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>メソッドの型を持つ<xref:EnvDTE.DTE>します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。  
  
## <a name="getting-the-dte-object"></a>DTE オブジェクトを取得します。  
  
#### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>DTE オブジェクトをサービス プロバイダーから取得するには  
  
1.  という名前の c# VSIX プロジェクトを作成する`DTETest`します。 エディター分類子の項目テンプレートを追加し、名前`DTETest`します。 詳細については、次を参照してください。[エディターの項目テンプレートを使用した拡張機能の作成](../extensibility/creating-an-extension-with-an-editor-item-template.md)です。  
  
2.  プロジェクトには、次のアセンブリ参照を追加します。  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3.  DTETest.cs ファイルに移動し、次の追加`using`ディレクティブ。  
  
    ```csharp  
    using EnvDTE;  
    using EnvDTE80;  
    using Microsoft.VisualStudio.Shell;  
  
    ```  
  
4.  `GetDTEProvider`クラスは、インポート、<xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>します。  
  
    ```csharp  
    [Import]  
    internal SVsServiceProvider ServiceProvider = null;  
  
    ```  
  
5.  `GetClassifier()` メソッドに次のコードを追加します。  
  
    ```csharp  
    DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
  
    ```  
  
6.  使用した場合、<xref:EnvDTE80.DTE2>インターフェイス、DTE オブジェクトをキャストすることができます。  
  
## <a name="see-also"></a>関連項目  
 [言語サービスとエディターの拡張ポイント](../extensibility/language-service-and-editor-extension-points.md)

