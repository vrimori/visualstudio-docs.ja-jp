---
title: オプションと [オプション] ページ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d85b900779a5df8af077b292b2e2f70b0592e35c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132932"
---
# <a name="options-and-options-pages"></a>オプションと [オプション] ページ
クリックすると**オプション**上、**ツール** メニューが開きます、**オプション** ダイアログ ボックス。 このダイアログ ボックスでオプションとして [オプション] ページと総称します。 すべてのカテゴリが [オプション] ページと、ナビゲーション ウィンドウのツリー コントロールにオプションのカテゴリが含まれます。 ページを選択すると、右側のウィンドウでそのオプションが表示されます。 これらのページを使用して、VSPackage の状態を決定するオプションの値を変更できます。  
  
## <a name="support-for-options-pages"></a>[オプション] ページのサポート  
 <xref:Microsoft.VisualStudio.Shell.Package>クラスは、[オプション] ページとオプションのカテゴリを作成するためのサポートを提供します。 <xref:Microsoft.VisualStudio.Shell.DialogPage>クラスは、[オプション] ページを実装します。  
  
 既定の実装<xref:Microsoft.VisualStudio.Shell.DialogPage>プロパティの汎用のグリッド内のユーザーにそのパブリック プロパティを提供します。 独自のユーザー インターフェイス (UI) を持つカスタム オプション ページを作成する ページで、さまざまなメソッドをオーバーライドすることで、この動作をカスタマイズできます。 詳細については、次を参照してください。[オプション ページを作成する](../../extensibility/creating-an-options-page.md)です。  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage>クラスが実装する<xref:Microsoft.VisualStudio.Shell.IProfileManager>の [オプション] ページおよびユーザー設定の永続性を提供します。 既定の実装、<xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A>と<xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A>プロパティは、文字列から変換できる場合、メソッドがレジストリのユーザー セクションにプロパティの変更を永続化します。  
  
## <a name="options-page-registry-path"></a>オプション ページのレジストリ パス  
 既定では、オプション ページによって管理されるプロパティのレジストリ パスは組み合わせによって決まります<xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>、word DialogPage、およびオプション ページのクラスの型名。 たとえば、次のようにオプション ページ クラスを定義できます。  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_1.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_1.vb)]  
  
 場合、 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp、プロパティの名前と値のペアは HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp\DialogPage\ のサブキーがCompany.OptionsPage.OptionsPageGeneral です。  
  
 オプション ページ自体のレジストリ パスを結合して特定は<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>単語、ToolsOptionsPages、およびオプション ページのカテゴリおよび名前です。 たとえば、カスタム オプション ページには、カテゴリ、マイ オプション ページ、および<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>オプション ページには、レジストリ キー hkey_local_machine \software\microsoft\ HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp がVisualStudio\8.0Exp\ToolsOptionsPages\My オプション Pages\Custom です。  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>ツール/オプション ページの属性とレイアウト  
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>属性のカスタム オプション ページのナビゲーション ツリー内のカテゴリにグループ化を決定する、**オプション** ダイアログ ボックス。 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>属性は、インターフェイスを提供する VSPackage のオプション ページを関連付けます。 次のコードがあるとします。  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_2.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_2.vb)]  
  
 これは、mypackage という 2 つのオプション ページ、OptionsPageGeneral および OptionsPageCustom が提供されているを宣言します。 **オプション**にダイアログ ボックスで、両方のオプション ページの表示、**マイ オプション ページ**としてカテゴリ**全般**と**カスタム**、それぞれします。  
  
## <a name="option-attributes-and-layout"></a>オプションの属性およびレイアウト  
 ページでは、ユーザー インターフェイス (UI) では、カスタム オプション ページのオプションの外観を決定します。 次の属性では、レイアウト、ラベル付け、および汎用オプション ページのオプションの説明が決定されます。  
  
-   <xref:System.ComponentModel.CategoryAttribute> オプションのカテゴリを決定します。  
  
-   <xref:System.ComponentModel.DisplayNameAttribute> オプションの表示名を決定します。  
  
-   <xref:System.ComponentModel.DescriptionAttribute> オプションの説明を指定します。  
  
    > [!NOTE]
    >  同等の属性、SRCategory、LocDisplayName、SRDescription、文字列リソースのローカライズ用と使用で定義されて、[マネージ プロジェクト サンプル](http://go.microsoft.com/fwlink/?LinkId=122774)です。  
  
 次のコードがあるとします。  
  
 [!code-csharp[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_3.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#3](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_3.vb)]  
  
 OptionInteger オプション ページに表示されます、オプションとして**整数オプション**で、 **My Options**カテゴリ。 オプションを選択する場合、説明、 **My 整数オプション**、[説明] ボックスに表示されます。  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>別の VSPackage から [オプション] ページにアクセスします。  
 ホストし、[オプション] ページを管理する VSPackage は、別の VSPackage からでプログラムによって、オートメーション モデルを使用してアクセスできます。 たとえば、次のコードでは、VSPackage はオプション ページをホストとして登録されます。  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_4.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_4.vb)]  
  
 次のコード フラグメントは、MyOptionPage から OptionInteger の値を取得します。  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/CSharp/options-and-options-pages_5.cs)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../extensibility/internals/codesnippet/VisualBasic/options-and-options-pages_5.vb)]  
  
 ときに、<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>属性は、[オプション] ページを登録、AutomationProperties 場合キーの下にあるページが登録されている、`SupportsAutomation`属性の引数は`true`します。 オートメーションでは、関連付けられている VSPackage とオートメーションを検索するには、このレジストリ エントリを調べし、ホスト型のオプション ページで、ここでは、個人用のページのグリッド プロパティにアクセスします。  
  
 結合することで、オートメーションのプロパティのレジストリ パスを決定<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>単語、AutomationProperties、およびオプション ページのカテゴリおよび名前です。 たとえば、次のオプション ページには、マイ カテゴリー、個人用のグリッド ページ名、および<xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp、しのオートメーション プロパティが、レジストリ キー hkey_local_machine \software\Microsoft\VisualStudio\8.0Exp\AutomationProperties\My Category\My グリッド ページです。  
  
> [!NOTE]
>  正規の名前、マイ Category.My グリッド ページでは、このキーの名前のサブキーの値です。