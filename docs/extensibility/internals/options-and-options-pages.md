---
title: "オプションと [オプション] ページ | Microsoft Docs"
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
  - "ツールのオプション ページ [Visual Studio SDK] が管理されているパッケージ フレームワークのサポート"
  - "パッケージの管理対象のフレームワーク、ツール オプション ページのサポート"
  - "ツール オプション ページのサポート"
  - "ツールのオプション] ページ [Visual Studio SDK] レイアウト"
  - "ツール オプション ページ [Visual Studio SDK] の属性"
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: 34
caps.handback.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
---
# オプションと [オプション] ページ
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

クリックすると **オプション** 上、 **ツール** メニューが開き、 **オプション** \] ダイアログ ボックス。 このダイアログ ボックスでオプションとして \[オプション\] ページと総称します。 すべてのカテゴリが \[オプション\] ページおよびナビゲーション ペインのツリー コントロールにはオプションのカテゴリが含まれます。 ページを選択すると、右側のウィンドウでそのオプションが表示されます。 これらのページでは、VSPackage の状態を確認するオプションの値を変更することができます。  
  
## \[オプション\] ページのサポート  
 <xref:Microsoft.VisualStudio.Shell.Package> クラスは、\[オプション\] ページとオプションのカテゴリを作成するためのサポートを提供します。<xref:Microsoft.VisualStudio.Shell.DialogPage> クラスは、\[オプション\] ページを実装します。  
  
 既定の実装 <xref:Microsoft.VisualStudio.Shell.DialogPage> プロパティの汎用のグリッド内のユーザーにそのパブリック プロパティを提供しています。 この動作をカスタマイズするには、ページを独自のユーザー インターフェイス \(UI\) を持つカスタム オプション ページを作成するさまざまなメソッドをオーバーライドします。 詳細については、「[オプション ページを作成します。](../../extensibility/creating-an-options-page.md)」を参照してください。  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage> クラスが実装する <xref:Microsoft.VisualStudio.Shell.IProfileManager>, の \[オプション\] ページおよびユーザー設定の永続化を提供します。 既定の実装、 <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> と <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> 文字列との間に、プロパティを変換できる場合、メソッドがレジストリの user\] セクションにプロパティの変更を永続化します。  
  
## オプション ページのレジストリ パス  
 既定では、オプション ページによって管理されるプロパティのレジストリ パスを結合することで確認は <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, 、word DialogPage、およびオプションのページ クラスの型名。 たとえば、次のようにオプション ページ クラスを定義できます。  
  
 [!CODE [VSSDKSupportForOptionsPages#1](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#1)]  
  
 場合、 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp、プロパティの名前と値のペアは HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp\\DialogPage\\Company.OptionsPage.OptionsPageGeneral のサブキーができます。  
  
 オプション ページ自体のレジストリ パスを結合することで確認 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, 、単語、ToolsOptionsPages、およびオプション ページのカテゴリおよび名前です。 たとえば、カスタムのオプション\] ページにカテゴリには、個人用のオプション ページおよび <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp、オプション ページには、レジストリ キー、HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp\\ToolsOptionsPages\\My オプション Pages\\Custom がします。  
  
## ツール\/オプション ページの属性とレイアウト  
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 属性のカスタム オプション ページのナビゲーション ツリーでのカテゴリにグループ化を決定する、 **オプション** \] ダイアログ ボックス。<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 属性は、インターフェイスを提供する VSPackage にオプション ページを関連付けます。 次のコードがあるとします。  
  
 [!CODE [VSSDKSupportForOptionsPages#2](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#2)]  
  
 これは、MyPackage が OptionsPageGeneral と OptionsPageCustom 2 つのオプション ページを提供することを宣言します。**オプション** にダイアログ ボックスで、両方のオプション ページの表示、 **オプション ページの \[マイ** とカテゴリ **全般的な** と **カスタム**, 、それぞれします。  
  
## オプションの属性とレイアウト  
 ページでは、ユーザー インターフェイス \(UI\) では、カスタム オプション ページのオプションの外観を決定します。 レイアウト、ラベル付け、および汎用オプション ページのオプションの説明は、次の属性によって決定されます。  
  
-   <xref:System.ComponentModel.CategoryAttribute> オプションのカテゴリを決定します。  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> オプションの表示名を決定します。  
  
-   <xref:System.ComponentModel.DescriptionAttribute> オプションの説明を指定します。  
  
    > [!NOTE]
    >  同等の属性、SRCategory、LocDisplayName、SRDescription、ローカリゼーション用の文字列リソースを使用およびで定義された、 [マネージ プロジェクト サンプル](http://go.microsoft.com/fwlink/?LinkId=122774)します。  
  
 次のコードがあるとします。  
  
 [!CODE [VSSDKSupportForOptionsPages#3](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#3)]  
  
 OptionInteger オプションとして \[オプション\] ページに表示されます **整数オプション** で、 **My Options** カテゴリ。 オプションが選択されている場合、説明、 **マイ整数オプション**, 、\[説明\] ボックスに表示されます。  
  
## 別の VSPackage から \[オプション\] ページにアクセスします。  
 VSPackage をホストし、\[オプション\] ページの管理は、別の VSPackage からでプログラムを使用してオートメーション モデルを使用してアクセスできます。 たとえば、次のコードでは、VSPackage はオプション ページをホストとして登録されます。  
  
 [!CODE [VSSDKSupportForOptionsPages#4](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#4)]  
  
 次のコード フラグメントでは、MyOptionPage から OptionInteger の値を取得します。  
  
 [!CODE [VSSDKSupportForOptionsPages#5](../CodeSnippet/VS_Snippets_VSSDK/vssdksupportforoptionspages#5)]  
  
 ときに、 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> 属性は、\[オプション\] ページを登録、AutomationProperties キーの場合\] の下に、ページが登録されている、 `SupportsAutomation` 属性の引数は `true`です。 オートメーションでは、関連付けられている VSPackage と自動化を検索するには、このレジストリ エントリを調べてし、ホストされているオプション\] ページで、この場合は、個人用のグリッド ページのプロパティにアクセスします。  
  
 オートメーション プロパティのレジストリ パスを結合することで確認 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, 、単語、AutomationProperties、およびオプション ページのカテゴリおよび名前です。 たとえば、次のオプション ページには My Category カテゴリには、個人用のグリッド ページ名、および <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>, 、HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp のオートメーション プロパティは、レジストリ キーを HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0Exp\\AutomationProperties\\My Category\\My グリッド ページを持ちます。  
  
> [!NOTE]
>  正規名、個人用の Category.My グリッド ページは、このキーの名前のサブキーの値です。