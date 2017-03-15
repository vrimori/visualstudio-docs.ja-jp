---
title: "オートメーションを使用した [オプション] ページの作成 | Microsoft Docs"
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
  - "[ツール オプション] ページ [Visual Studio SDK]、作成"
  - "オートメーション [Visual Studio SDK]、[ツール オプション] ページの作成"
ms.assetid: 05ec0337-58fe-4746-8e85-7fb97f285522
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# オートメーションを使用した [オプション] ページの作成
マネージ VSPackage は ENT2ENT \[入力\] メニューに  **オプション**  のページを追加することに \(IDE\) よって [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の統合開発環境を拡張するにはオートメーションを使用できます。  
  
 \[入力\] ENT0ENT ページの基本的なユーザー コントロールには他のユーザー コントロールと同様にコードされます。  通常オブジェクトを作成しユーザー コントロールを追加するには [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE の 1 人を使用します。  
  
> [!NOTE]
>  Windows メッセージを処理するように `DialogProc` を使用してダイアログ ボックスとして実装される **\*\*\* Tools Options \*\*\*** のページはモードレス ダイアログ ボックスであり `EndDialog` 関数を呼び出すことはできません。  
  
 VSPackage をサポートするユーザー コントロールのプロパティに環境に提供するオートメーション オブジェクトを使用する必要があります。  
  
## 相互運用機能アセンブリで実装されるツール オプション ページのオートメーションのサポート  
 オートメーション モデルをサポートするにはVSPackageオートメーション オブジェクトを作成および登録する必要があります。  詳細については、「[Vspackage のための自動化を提供します。](../extensibility/internals/providing-automation-for-vspackages.md)」を参照してください。  
  
 オートメーション モデルを使用するコードを特定の ENT0ENT \[入力\] ページのプロパティのコレクションの `DTE.Properties` を呼び出すとコレクションを返し<xref:EnvDTE.Property> 構成オブジェクトへのアクセスを許可する VSPackage の <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> の実装によって提供されるオートメーション オブジェクトを使用します。  
  
 VSPackage \(\) が複数のオートメーション オブジェクトをサポートできるように <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> によって返されるオートメーション オブジェクトに依存指定された GUID に依存します。  オートメーション オブジェクトの実装の詳細については[オートメーション \[オプション\] ページのサポート](../Topic/Automation%20Support%20for%20Options%20Pages.md) を参照してください。  
  
 \[入力\] ENT0ENT ページの 2 種類の識別子を指定します。  最初の識別子を含むフォルダーを ENT1ENT \[入力\] メニューの \[ENT0ENT\] セクションの項目を示す文字列です。  2 番目の識別子はフォルダー内の特定の項目を示す文字列です。  詳細については、「[\[オプション\] ページの使用](../Topic/Using%20Options%20Pages.md)」を参照してください。  
  
 2 個のレジストリ エントリはオートメーション オブジェクトを登録する必要があります :  
  
-   HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<Version* \\Packages\\*\<PackageGUID\>*\\Automation オートメーションの下  
  
-   HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\ \\ AutomationProperties の下  *\<Version\>*  
  
     *\<Version\>*  が [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のバージョンのに対し\(8.0\) と  *\<PackageGUID\>*  はオートメーション オブジェクトを実装する VSPackage の GUID です。  
  
 AutomationProperties のレジストリ エントリの下の構成によっては\[ENT0ENT ページの状態は [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の構成機能を使用してユーザーが ENT2ENT \[入力\] メニューの **\*\*\* Import\/Export Settings \*\*\*** のコマンドを選択したときに自動的に保存および復元方法があります。  \[入力\] ENT0ENT ページの設定を保存する方法の詳細については[カスタム オプション ページの登録](../misc/registering-custom-options-pages.md) を参照してください。  
  
 アプリケーションは **\*\*\* Tools Options \*\*\*** ページのプロパティと設定のサポートを実装するためにオートメーション モデルを使用できないことがあります。  
  
 これは複数の原因である可能性があります :  
  
-   \[入力\] ENT9ENT ページによって処理される設定が比較的フラットなオートメーション モデルのプロパティがサポートするものを構造体により複雑です。  
  
-   他のアプリケーションがプログラムで \[入力\] ページ ENT0ENT 管理されるのを防ぐ必要があります。  
  
-   特別なアクセスを制御するセキュリティ機能が必要です。  
  
 このような場合VSPackage が適切であるかどう ENT0ENT \[入力\] ページのサポートを実装できます。  ただしあります :  
  
-   \[入力\] ENT0ENT ページのプロパティの設定を処理します。  
  
-   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 設定に ENT2ENT \[入力\] ページの状態の永続性を管理します。  
  
-   \[入力\] ENT0ENT ページを使用する他のアプリケーションの API を必要に応じて提供します。  
  
 \[入力\] ENT0ENT ダイアログ ボックスのプロパティはオートメーション モデルで変更できない ENT1ENT \[入力\] ページの例です。  代わり ENT1ENT \[入力\] ページの  **フォントおよび色**  のプログラムによる操作を可能にするには別の API は <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> のインターフェイスに基づいて提供されます。  \[入力\] ENT1ENT ページの  **フォントおよび色**  制御の詳細については[フォントおよび色を使用します。](../extensibility/using-fonts-and-colors.md) を参照してください。  
  
## マネージ パッケージ フレームワーク内のツール オプション ページのオートメーションのサポート  
 示すように実装の登録 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> のインスタンスの <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A> のプロパティを \[ENT2ENT ページのサポートのオートメーションのマネージ パッケージの .NET Framework ベースの実装に設定します。  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> から派生した **\*\*\* Tools Options \*\*\*** ページがオーバーライドできる既定のオートメーション オブジェクトに格納されます。  
  
 \[入力\] ENT0ENT ページの実装がオートメーションをサポートする実装では\[ENT1ENT のページへのプログラムによるアクセスに独自の API を提供する必要があります。  
  
> [!NOTE]
>  \[入力\] ENT0ENT ページの IDE'S はオートメーションをサポートしないが\[ENT2ENT ページの状態へのアクセスを提供する独自の API ENT1ENT \[入力\] ページに示します。  詳細については、「[フォントおよび色を使用します。](../extensibility/using-fonts-and-colors.md)」を参照してください。  
  
## 参照  
 [Extending the Visual Studio Environment](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)   
 [相互運用機能アセンブリを使用した \[オプション\] ページの作成](../Topic/Creating%20Options%20Pages%20By%20Using%20Interop%20Assemblies.md)   
 [\[オプション\] ページを作成します。](../Topic/Creating%20Options%20Pages.md)   
 [How to: Create Custom Options Pages](../Topic/How%20to:%20Create%20Custom%20Options%20Pages.md)   
 [レジストラー スクリプトの作成](/visual-cpp/atl/creating-registrar-scripts)   
 [オートメーション \[オプション\] ページのサポート](../Topic/Automation%20Support%20for%20Options%20Pages.md)   
 [\[オプション\] ページの使用](../Topic/Using%20Options%20Pages.md)