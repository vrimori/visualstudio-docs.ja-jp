---
title: "設定カテゴリのサポート | Microsoft Docs"
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
  - "設定、Visual Studio SDK によるサポート"
  - "Visual Studio SDK、設定のサポート"
ms.assetid: 3bac375d-8bd5-41be-a8de-32eb33c5cfac
caps.latest.revision: 20
caps.handback.revision: 20
manager: "douge"
---
# 設定カテゴリのサポート
設定カテゴリは統合開発環境 \(IDE\) をカスタマイズするためのグループで構成されます。 たとえば設定により、メニューの [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のウィンドウとコンテンツのレイアウトを制御できます。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
 **\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックし、**設定のインポートとエクスポート ウィザード**を開始します。 ウィザードには、設定のエクスポート、インポート、リセットという 3 つの選択肢があります。 たとえば、エクスポートを選択すると、ウィザードの **\[エクスポートする設定の選択\]** ページが表示されます。  
  
 このページのナビゲーション ウィンドウには、ツリー コントロールにカテゴリが表示されます。 カテゴリは、"カスタム設定ポイント" という関連する設定 \(チェック ボックス\) のグループです。 これらのチェック ボックスを使用して、.vsettings ファイルに保持するカテゴリを選択します。 ウィザードでは、.vsettings ファイルに名前を付け、パスを指定することができます。  
  
> [!NOTE]
>  設定はカテゴリとして保存または復元されます。また、個々の設定名はウィザードに表示されません。  
  
 Managed Package Framework \(MPF\) は、最小限の追加コードでの設定カテゴリの作成をサポートしています。  
  
-   <xref:Microsoft.VisualStudio.Shell.Package> クラスをサブクラス化して、カテゴリのコンテナーとして使用するには、VSPackage を作成します。  
  
-   カテゴリ自体を作成するには、<xref:Microsoft.VisualStudio.Shell.DialogPage> クラスから派生させます。  
  
-   これら 2 つは <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> で接続します。  
  
## 設定カテゴリのサポート  
 <xref:Microsoft.VisualStudio.Shell.Package> クラスは、カテゴリの作成をサポートしています。<xref:Microsoft.VisualStudio.Shell.DialogPage> クラスは、カテゴリを実装しています。<xref:Microsoft.VisualStudio.Shell.DialogPage> の既定の実装では、カテゴリとしてパブリック プロパティがユーザーに提供されます。 詳細については、「[設定のカテゴリを作成します。](../extensibility/creating-a-settings-category.md)」を参照してください。  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> クラスは <xref:Microsoft.VisualStudio.Shell.IProfileManager> を実装しており、オプション ページとユーザー設定の両方について保持機能を提供しています。<xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> メソッドと <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> メソッドは、設定を .vssettings ファイルに保持します。このファイルは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] がそれぞれ <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> または <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> として提供します。<xref:Microsoft.VisualStudio.Shell.IProfileManager.ResetSettings%2A> メソッドは、設定を既定値にリセットします。  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> クラスを使用すると、xml フィードから名前と値のペアを読み取り、反映を使用して <xref:Microsoft.VisualStudio.Shell.DialogPage> 派生クラスのパブリック プロパティを検出する <xref:Microsoft.VisualStudio.Shell.DialogPage.LoadSettingsFromXml%2A> メソッドを実装できます。 名前と値のペアと一致する名前を持つプロパティには、対応する値が指定されます。  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage.SaveSettingsToXml%2A> の既定の実装では、反映を使用して <xref:Microsoft.VisualStudio.Shell.DialogPage> 派生クラスのパブリック プロパティを検出し、プロパティ名と値を名前と値のペアとして XML フィードに出力します。  
  
### 設定カテゴリのレジストリ パス  
 設定カテゴリのレジストリ パスは、<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>、単語、UserSettings、設定カテゴリ、カスタム設定ポイントの名前の組み合わせで決まります。 設定カテゴリとカスタム設定ポイントの名前は、アンダースコア区切りでレジストリに表示されるローカライズされない正規名の形式に結合されます。 たとえば、設定カテゴリが "My Category"、カスタム設定ポイント名が "My Settings"、ApplicationRegistryRoot が HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp の場合、設定カテゴリのレジストリ キーは HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp\\UserSettings\\My Category\_My Settings になります。  
  
> [!NOTE]
>  正規名はユーザー インターフェイス \(UI\) に表示されません。 正規名は、プログラム ID \(ProgID\) と同様に、判読できる名前を設定カテゴリに関連付けるために使用されます。  
  
### 設定カテゴリの属性  
 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> によって、提供する VSPackage とカテゴリが関連付けられることで、**設定のインポートとエクスポート ウィザード**でカスタム設定ポイントへのカテゴリのマッピングが決まります。 次のコードがあるとします。  
  
 [!code-vb[VSSDKSupportForSettingsCategories#1](../misc/codesnippet/VisualBasic/support-for-settings-categories_1.vb)]
 [!code-cs[VSSDKSupportForSettingsCategories#1](../misc/codesnippet/CSharp/support-for-settings-categories_1.cs)]  
  
 リソース ID 106 は "My Category" に、107 は "My Settings" に、108 は "Various Options" にマッピングされます。 これは、`MyPackage` がカテゴリ My Category\_My Settings を提供するという宣言です。 カテゴリは `OptionsPageGeneral` クラスから提供されます。この場合、<xref:Microsoft.VisualStudio.Shell.IProfileManager> を実装する必要があります。 このカテゴリの設定は、`OptionsPageGeneral` クラスのパブリック プロパティです。  
  
 **設定のインポートとエクスポート ウィザード**で、設定ポイントの名前は "My Settings" です。 設定ポイントを選択すると、"**さまざまなオプション**" という説明が表示されます。 設定ポイント名と説明は、ローカライズされた文字列リソースから取得されます。  
  
## 参照  
 [オプション ページを作成します。](../extensibility/creating-an-options-page.md)   
 [VSSDK のサンプル](../misc/vssdk-samples.md)   
 [Visual Studio の状態](/visual-cpp/misc/vspackage-state)   
 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)