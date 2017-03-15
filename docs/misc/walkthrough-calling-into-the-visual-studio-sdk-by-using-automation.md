---
title: "チュートリアル: オートメーションを使用した Visual Studio SDK の呼び出し | Microsoft Docs"
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
  - "チュートリアル [Visual Studio SDK]、オートメーションを使用した呼び出し"
ms.assetid: ca4dab48-632c-4c2a-8c84-57c027e37987
caps.latest.revision: 31
caps.handback.revision: 31
manager: "douge"
---
# チュートリアル: オートメーションを使用した Visual Studio SDK の呼び出し
このチュートリアルでは、Visual Studio サービスを使用する Visual Studio アドインを作成する方法について説明します。 作成するアドインはサービス プロバイダーを取得し、それを使用してサービスを取得します。 これと同じ手法を使用して、提供されるすべての Visual Studio サービスを取得できます。 サービスおよびサービス プロバイダーの詳細については、「[使用して、サービスを提供します。](../extensibility/using-and-providing-services.md)」を参照してください。 次の手順では、アドインを作成し、アドインからサービスを取得する方法を示します。  
  
## アドインの作成  
 このセクションでは、Visual Studio アドイン プロジェクト テンプレートを使用して Visual Studio アドインを作成します。  
  
#### アドインを作成するには  
  
1.  新しい Visual Studio プロジェクトを作成します \(**\[ファイル\]\/\[新規作成\]\/\[プロジェクト\]**\)。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスの左ペインで、**\[その他のプロジェクトの種類\]** ノードを展開し、**\[機能拡張\]** ノードをクリックします。**\[Visual Studio アドイン\]** を選択します。  
  
3.  `Addin` という名前の新しいアドイン プロジェクトを作成します。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] アドイン ウィザードで **\[次へ\]** をクリックします。  
  
4.  **\[プログラミング言語の選択\]** ページで、**\[Visual C\# を使用してアドインを作成\]** または **\[Visual Basic を使用してアドインを作成\]** を選択します。  
  
5.  **\[アプリケーション ホストの選択\]** ページで、**\[Microsoft Visual Studio \<version\>\]** を選択します。  
  
6.  **\[名前および説明の入力\]** ページで、**\[名前\]** ボックスに「`MyAddin`」と入力し、**\[説明\]** ボックスに「`MyAddin Walkthrough`」と入力します。  
  
7.  **\[アドイン オプションを選択します。\]** ページで、**\[アドイン用のコマンド バー UI を作成しますか?\]** で \[ツール\] メニュー項目のオプションを選択します。 その他のチェック ボックスをオフにします。  
  
8.  その他のすべての既定値をそのまま使用します。  
  
9. ソリューションをビルドし、エラーが発生することなくソリューションがコンパイルされることを確認します。  
  
## アドインからのサービスの取得  
 次の手順に従って、アドインからサービスを取得します。  
  
#### サービスを取得するには  
  
1.  Connect.cs または Connect.vb ファイルを開き、次の行を `using` \(C\#\) または `Imports` \(Visual Basic\) ステートメントに追加します。  
  
     [!CODE [VSSDKAddin#1](../CodeSnippet/VS_Snippets_VSSDK/vssdkaddin#1)]  
  
2.  **ソリューション エクスプローラー**でプロジェクト ノードを右クリックし、次の .NET 参照を追加します。  
  
    ```  
    Microsoft.VisualStudio.OLE.Interop Microsoft.VisualStudio.Shell.Interop  
    ```  
  
3.  次のコード行を `Exec` メソッドの `if(commandName == "Addin.Connect.Addin")` または `If commandName = "Addin.Connect.Addin" Then` 句に追加します。  
  
     [!CODE [VSSDKAddin#2](../CodeSnippet/VS_Snippets_VSSDK/vssdkaddin#2)]  
  
     このコードは、現在のアプリケーション オブジェクト \(型 `DTE2`\) を `IOleServiceProvider` にキャストし、`QueryService` を呼び出して <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> サービスを取得します。 このサービスは <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> インターフェイスを提供します。 アドインが実行されると、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> メソッドはメッセージ ボックスを表示します。  
  
4.  F5 キーを押してデバッグ モードで Addin プロジェクトをビルドし、開始します。  
  
     これにより、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の別のインスタンスが開始します。  
  
5.  新しい [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] インスタンスで、**\[ツール\]** メニューの **\[Addin\]** をクリックします。 メッセージ ボックスに次のように表示されます。  
  
    ```  
    MyAddin Inside Addin.Connect  
    ```  
  
## 参照  
 [How to: Deactivate and Remove an Add\-In](../Topic/How%20to:%20Deactivate%20and%20Remove%20an%20Add-In.md)