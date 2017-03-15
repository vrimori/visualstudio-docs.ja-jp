---
title: "チュートリアル: オートメーションを使用したマネージ VSPackage の拡張 | Microsoft Docs"
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
  - "マネージ VSPackage、オートメーションを使用した拡張"
  - "オートメーション [Visual Studio SDK]、チュートリアル"
  - "オートメーション [Visual Studio SDK]、マネージ VSPackage"
ms.assetid: 7fd2000b-8ec3-4d83-b169-d38008fb57ee
caps.latest.revision: 35
caps.handback.revision: 35
manager: "douge"
---
# チュートリアル: オートメーションを使用したマネージ VSPackage の拡張
このチュートリアルでは、オートメーションを使用して、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 統合開発環境 \(IDE\) を操作するマネージ VSPackage を作成する方法を示します。 サンプルのマネージ VSPackage を作成し、その結果として得られる VSPackage でオートメーション メソッドを使用して **\[出力\]** ウィンドウに [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロパティを表示します。  
  
## 必須コンポーネント  
 このチュートリアルに従うには、Visual Studio SDK をインストールする必要があります。 詳細については、「[Visual Studio SDK](../extensibility/visual-studio-sdk.md)」を参照してください。  
  
## Visual Studio パッケージのプロジェクト テンプレートの場所  
 Visual Studio パッケージのプロジェクト テンプレートは、**\[新しいプロジェクト\]** ダイアログの次の 3 つの場所にあります。  
  
1.  Visual Basic の機能拡張の下。 プロジェクトの既定の言語は Visual Basic です。  
  
2.  C\# の機能拡張の下。 プロジェクトの既定の言語は C\# です。  
  
3.  その他のプロジェクトの種類の機能拡張の下。 プロジェクトの既定の言語は C\+\+ です。  
  
### マネージ VSPackage を作成するには  
  
1.  `Auto` という名前で [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] パッケージ プロジェクトを作成します。  
  
     マネージ VSPackage を作成する方法の詳細については、「[チュートリアル: Visual Studio パッケージ テンプレートを使用してメニュー コマンドを作成する](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md)」を参照してください。  
  
2.  **\[プログラミング言語の選択\]** ページで、言語を [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] に設定します。  
  
3.  **\[基本的な Visual Studio パッケージに関する情報\]** ページで既定値を保持します。  
  
4.  **\[Visual Studio パッケージのオプションの選択\]** ページで、**\[メニュー コマンド\]** チェック ボックスをオンにします。  
  
5.  **\[コマンド オプション\]** ページで、**\[コマンド名\]** を `Auto` に変更します。  
  
6.  **\[完了\]** ボタンをクリックします。  
  
     Auto という名前でマネージ プロジェクトが生成されます。  
  
7.  ソリューションをビルドし、エラーが発生することなくソリューションがコンパイルされることを確認します。  
  
### オートメーション モデルを呼び出すには  
  
1.  **ソリューション エクスプローラー**で \[Auto\] プロジェクト ノードを右クリックし、**\[追加\]**、**\[参照\]** の順にクリックします。  
  
2.  **\[参照\]** ダイアログ ボックスの **\[.NET\]** タブで、**\[EnvDTE\]** をダブルクリックします。  
  
     EnvDTE オートメーション名前空間への参照が追加されます。  
  
3.  AutoPackage ファイルで、次の名前空間参照を追加します。  
  
     [!code-cs[VSSDKAuto#1](../misc/codesnippet/CSharp/walkthrough-extending-managed-vspackages-by-using-automation_1.cs)]
     [!code-vb[VSSDKAuto#1](../misc/codesnippet/VisualBasic/walkthrough-extending-managed-vspackages-by-using-automation_1.vb)]  
  
4.  AutoPackage ファイルで、`MenuItemCallback` メソッドの本体を次の行に置き換えます。  
  
     [!code-cs[VSSDKAuto#2](../misc/codesnippet/CSharp/walkthrough-extending-managed-vspackages-by-using-automation_2.cs)]
     [!code-vb[VSSDKAuto#2](../misc/codesnippet/VisualBasic/walkthrough-extending-managed-vspackages-by-using-automation_2.vb)]  
  
 このコードは、<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> を呼び出して、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE を表す <xref:EnvDTE.DTE> オートメーション オブジェクトを取得します。`MenuItemCallback` のオートメーション コードは、**\[出力\]** ウィンドウに **\[テスト\]** という名前で新しいウィンドウを作成します。 この新しい **\[出力\]** ウィンドウに [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の名前とバージョンが書き込まれます。  
  
1.  F5 キーを押してデバッグ モードで Auto プロジェクトをビルドし、開始します。  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 試験的ビルド \([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Exp\) が起動します。  
  
    > [!NOTE]
    >  この時点では [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の両方のバージョンが開いています。  
  
2.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Exp の **\[ツール\]** メニューで、**\[Auto\]** をクリックします。  
  
     **\[出力\]** ウィンドウに **\[テスト\]** という名前の新しいウィンドウが開き、次の情報が表示されます。  
  
    ```  
    Name is Microsoft Visual Studio Version is x.xx  
    ```  
  
     ここで、x.xx は [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の最新のバージョン番号です。  
  
     オートメーションのサンプルの詳細については、[Visual Studio のオートメーションのサンプル](http://www.microsoft.com/downloads/details.aspx?familyid=3ff9c915-30e5-430e-95b3-621dccd25150&displaylang=en)を参照してください。  
  
## 参照  
 [Extending the Visual Studio Environment](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)