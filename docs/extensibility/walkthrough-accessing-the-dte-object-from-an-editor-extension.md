---
title: 'チュートリアル: エディター拡張機能から DTE オブジェクトにアクセスする |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - getting the DTE object
ms.assetid: c1f40bab-c6ec-45b0-8333-ea5ceb02a39d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8ed4343139b3e59dfba7adc71b1c91cdf01c13db
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586249"
---
# <a name="walkthrough-accessing-the-dte-object-from-an-editor-extension"></a>チュートリアル: エディター拡張機能から DTE オブジェクトにアクセスします。
Vspackage では、呼び出すことによって、DTE オブジェクトを取得できます、 <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> DTE オブジェクトの型を持つメソッド。 Managed Extensibility Framework (MEF) 拡張機能でインポートできる<xref:Microsoft.VisualStudio.Shell.SVsServiceProvider>を呼び出して、<xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A>メソッドの型を持つ<xref:EnvDTE.DTE>します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、次を参照してください。 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)します。  
  
## <a name="getting-the-dte-object"></a>DTE オブジェクトを取得します。  
  
### <a name="to-get-the-dte-object-from-the-serviceprovider"></a>DTE オブジェクトをサービス プロバイダーから取得するには  
  
1.  という名前の c# VSIX プロジェクトを作成する`DTETest`します。 エディター分類子の項目テンプレートを追加し、名前`DTETest`します。 詳細については、次を参照してください。[エディターの項目テンプレートを使用した拡張機能を作成する](../extensibility/creating-an-extension-with-an-editor-item-template.md)します。  
  
2.  プロジェクトには、次のアセンブリ参照を追加します。  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Microsoft.VisualStudio.Shell.Immutable.10.0  
  
3.  移動して、 *DTETest.cs*ファイルを開き、次の追加`using`ディレクティブ。  
  
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