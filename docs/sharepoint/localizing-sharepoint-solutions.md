---
title: SharePoint ソリューションのローカライズ |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.GlobalAndFeatureResource
- VS.SharePoint.Project.AddResourceDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- globalizing [SharePoint development in Visual Studio]
- localizing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ba02d8811fc6633a55e06ae63c9399c70f59634f
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119847"
---
# <a name="localize-sharepoint-solutions"></a>SharePoint ソリューションをローカライズします。

  アプリケーションを世界中で使用できるように準備するプロセスをローカライズと呼びます。 ローカライズでは、リソースを特定のカルチャに翻訳します。 詳細については、次を参照してください。 [Globalizing and Localizing Applications](/visualstudio/ide/globalizing-and-localizing-applications)します。 このトピックでは、SharePoint ソリューションをローカライズする方法の概要について説明します。  
  
 ソリューションをローカライズするには、ハードコーディングされた文字列をコードから削除してリソース ファイルに抽出します。 リソース ファイルとは、 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]-ベースのファイルで、 *.resx*拡張機能。 リソース ファイルには、ソリューションで使用される文字列の翻訳されたバージョンが含まれています。 詳細については、次を参照してください。[アプリケーションのリソース](http://go.microsoft.com/fwlink/?LinkID=155844)します。  
  
> [!NOTE]  
>  SharePoint ソリューションのリソース ファイルに追加するのは文字列リソースだけです。 リソース エディターでは文字列以外のリソースも追加できますが、文字列以外のリソースは SharePoint に配置されません。  
  
## <a name="resource-files"></a>リソース ファイル
 リソース ファイルには、既定のリソース ファイル、言語に依存しないリソース ファイル、および言語固有のリソース ファイルの 3 種類があります。  
  
|リソース ファイルの種類|説明|  
|------------------------|-----------------|  
|既定値|フォールバック リソースとも呼ばれます。既定のリソース ファイルには、既定のカルチャ (英語など) にローカライズされた文字列が含まれます。 これらは、指定された言語のローカライズされたリソース ファイルが見つからない場合に使用されます。 既定のリソースは、独立したファイルを持たず、メイン アプリケーション アセンブリに格納されます。|  
|言語に依存しないリソース ファイル|特定の言語にはローカライズされているが特定のカルチャにはローカライズされていない文字列を含むリソース ファイル  (たとえば、フランス語の場合は "fr")。|  
|言語固有のリソース ファイル|特定の言語とカルチャにローカライズされた文字列を含むリソース ファイル  (たとえば、フランス語 (カナダ) の場合は "fr-CA")。|  
  
 詳細については、次を参照してください。[ローカリゼーション用リソースの階層編成](http://go.microsoft.com/fwlink/?LinkId=178360)します。  
  
 開発する SharePoint プロジェクトで既定のリソース ファイルを指定する[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、選択**インバリアント言語 (国のインバリアント)** カルチャの一覧で、**リソースの追加** ダイアログ ボックスの場合にします。リソース ファイルを追加します。  
  
## <a name="localize-visual-studio-sharepoint-solutions"></a>Visual Studio SharePoint ソリューションをローカライズします。
 ソリューションをローカライズする際には、そのソリューションでユーザーに表示されるすべてのテキスト情報を考慮に入れる必要があります。 たとえば、情報メッセージ、エラー メッセージ、および [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] 文字列を翻訳して、リソース ファイルに配置する必要があります。  
  
 リソース ファイルでは、すべての文字列に一意の識別子があります。 翻訳した文字列に対しては、各リソース ファイルで同じ識別子を使用する必要があります。 たとえば、既定のリソース ファイルの最初の文字列の識別子が "String1" だった場合は、言語固有のリソース ファイルの最初の文字列の識別子も "String1" にします。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint アプリケーションでは、フィーチャー、ASPX ページ マークアップ、およびコードの 3 つの領域をローカライズするのが一般的です。 以降の説明では、SharePoint ソリューションをドイツ語と日本語にローカライズする場合を想定しています。 既定の言語は英語です。  
  
### <a name="localize-features"></a>機能をローカライズします。
 フィーチャーをローカライズするには、ハードコーディングされたフィーチャーのタイトルと説明を、ローカライズされたリソース ファイルに含まれている翻訳済みのタイトルと文字列を参照する式に置き換える必要があります。 この変更を行う、**フィーチャー デザイナー**で[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。 詳細については、次を参照してください。[方法: フィーチャーをローカライズ](../sharepoint/how-to-localize-a-feature.md)します。  
  
 英語のフィーチャーをドイツ語と日本語にローカライズするには、プロジェクトに 3 つのリソース ファイル プロジェクト項目 (英語用、ドイツ語用、および日本語用) を追加します。 フィーチャー リソース ファイルは、ASPX マークアップやコードのローカライズには使用できません。これらにはまた別のリソース ファイルが必要です。  
  
 フィーチャー リソース ファイルを作成したら、そこに翻訳済みの文字列を追加します。 ローカライズされた文字列にアクセスするには次の形式の式を使用します。  
  
```aspx-csharp  
$Resources:String ID  
```  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] のフィーチャー リソースの名前は常に Resources です。 ロケールに依存しない言語以外を選択した場合、リソース ファイル名にカルチャ [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] が追加されます。 たとえば、インバリアント言語 (既定値) フィーチャー リソース ファイルを追加すると、呼び出されます*Resources.resx*します。 日本語 (日本) のカルチャを選択して、言語固有のフィーチャー リソースを追加する場合、ファイルが呼び出されます*Resources.ja-jp.resx になります*します。 フィーチャー リソース ファイルの名前は自動的に割り当てられ、変更することはできません。  
  
 フィーチャー リソースのスコープは、追加先のフィーチャーのローカル スコープです。 ソリューション内のすべての機能や要素ファイルで使用できるリソースを作成するには追加、**グローバル リソース ファイル**フィーチャー リソース ファイルではなくプロジェクト アイテム。 **グローバル リソース ファイル**プロジェクトの項目が内にある、 **2010**の下のフォルダー **SharePoint**で、**新しい項目の追加** ダイアログ ボックス。 グローバル リソース ファイルは、SharePoint ルート フォルダーの \Resources フォルダーに配置されます。  
  
### <a name="localize-aspx-page-markup"></a>ASPX ページ マークアップをローカライズします。
 ローカライズする[!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]ページ、プロジェクトに次の 3 つのリソース ファイル プロジェクト項目を追加する: 英語用、ドイツ語用、および日本語の 1 つ。 マークアップに加えてコードをローカライズする必要はない場合、は、グローバル リソース ファイルを代わりに追加できます。  
  
 既定の言語のリソース ファイルに任意の名前を付けます。 ローカライズされたリソース ファイルに対しては、同じ名前に言語固有のカルチャ [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] を加えた名前を使用します  たとえば、 *MyAppResources.de」という*ドイツ語と*MyAppResources.ja になります*日本語。  
  
 設定、**展開の種類**プロパティには、各リソース ファイルの**AppGlobalResource**します。 これにより、リソース ファイルが App_GlobalResources フォルダーに配置されます。このフォルダーに配置されたリソース ファイルは、ソリューション内のすべての ASPX ページと ASPX コントロールで使用できます。 App_GlobalResources フォルダー C:\inetpub\wwwroot\wss\VirtualDirectories で\\< ポート番号\>\App_GlobalResources します。  
  
> [!NOTE]  
>  グローバルではないリソース ファイルを使用する場合は、それらをプロジェクト項目フォルダーに移動します。これにより、[配置タイプ] プロパティやその他の SharePoint 固有のプロパティを使用できるようになります。  
  
 ASPX マークアップ リソース ファイルは、コードのローカライズにも使用できます。 リソースを ASPX マークアップだけでなくコードのローカライズにも使用する場合は、各ファイルの [ビルド アクション] プロパティの設定を [埋め込まれたリソース] のままにして、リソースがサテライト アセンブリにコンパイルされるようにします。 リソース ファイルをマークアップのローカライズのみに使用する場合は、[ビルド アクション] プロパティを [コンテンツ] に変更して、ファイルがメイン アプリケーション アセンブリにコンパイルされないようにすることもできます。  
  
 ASPX ページと ASPX コントロールのマークアップで、ハードコーディングされたプロパティ文字列をすべて次の形式の式に置き換えます。  
  
```aspx-csharp  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 例えば:  
  
```aspx-csharp  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 テキストとしての ASPX に対しては次の形式の式を使用します。  
  
```aspx-csharp  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 例えば:  
  
```aspx-csharp  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 詳細については、次を参照してください。[方法: ローカライズの ASPX マークアップ](../sharepoint/how-to-localize-aspx-markup.md)します。  
  
### <a name="localize-code"></a>コードをローカライズします。
 フィーチャーの文字列と [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] のマークアップに加えて、ソリューション コード内のメッセージ文字列やエラー文字列をローカライズする必要もあります。 ローカライズされた情報とエラー メッセージはサテライト アセンブリに格納されます。 サテライト アセンブリには、[!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] テキストや例外出力メッセージなど、ユーザーに表示される文字列が格納されます。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] では、.NET Framework の標準のハブ アンド スポーク モデルが使用されており、 ハブ (メイン プログラム アセンブリ) に既定の言語リソースが含まれ、 スポーク、またはサテライト アセンブリ、言語固有のリソースを含めます。 詳細については、「[リソースのパッケージ化と配置](http://go.microsoft.com/fwlink/?LinkId=179280)」を参照してください。 リソースからサテライト アセンブリがコンパイルされます (*.resx*) ファイル。 言語固有のリソース ファイル、プロジェクトと、ソリューション パッケージを追加するときに[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]という名前のサテライト アセンブリにリソース ファイルをコンパイル*プロジェクト {name}.resources.dll*します。  
  
 SharePoint アプリケーションのコードをローカライズするには、ASPX マークアップの場合と同様に、既定の言語用と各ローカライズ言語用の個別のリソース ファイル プロジェクト項目をプロジェクトに追加します。 ただし、前述のとおり、ASPX マークアップのローカライズ用のリソース ファイルが既にある場合は、それらをコードのローカライズに再利用できます。 リソース ファイルを作成する必要がある場合、既定の言語リソース ファイルの名前が付いた任意の *.resx*拡張機能。 ローカライズされたリソース ファイルに対しては、同じ名前に言語固有のカルチャ [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] を加えた名前を使用します。 各リソース ファイルの [ビルド アクション] プロパティを [埋め込まれたリソース] に設定して、サテライト リソース アセンブリが作成されるようにします。  
  
 サテライト アセンブリを作成するプロジェクトをビルドし、追加のアセンブリとしてファイルを追加して、**詳細**のタブ、**パッケージ デザイナー**します。 アセンブリを追加するときに、カルチャを付加[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]、場所のパスにフォルダーなど*DE-DE\\{プロジェクト項目名}.resources.dll*します。 これにより、同じ名前の複数のファイルをパッケージに含めることができます。  
  
 コードで次の構文を使用して、ハードコーディングされた文字列を <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> メソッドの呼び出しに置き換えます。  
  
```aspx-csharp  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 詳細については、次を参照してください。[方法: コードのローカライズ](../sharepoint/how-to-localize-code.md)します。  
  
#### <a name="web-part-code-localization"></a>Web パーツ コードのローカライズ
 Web パーツに含まれるカスタム プロパティ エディター機能には、ハードコーディングされた文字列を使用するコード属性 (WebDisplayName、Category、WebDescription など) が含まれています。 これらの属性の文字列値を置き換えるには、属性のクラスから派生する別のクラスを作成して、 それらのクラスで属性のプロパティを設定します。 属性のプロパティは基底クラスに依存します。 たとえば、WebDisplayName 属性のプロパティは DisplayNameValue で、WebDescription 属性のプロパティは DescriptionValue です。  
  
 派生クラスで、リソース ファイルの文字列 ID と ResourceManager オブジェクトを参照してその文字列 ID のローカライズされた値を取得し、 その値をプロパティ エディターの属性に返します。  
  
## <a name="see-also"></a>関連項目
 [方法: フィーチャーをローカライズ](../sharepoint/how-to-localize-a-feature.md)   
 [方法: ASPX マークアップのローカライズ](../sharepoint/how-to-localize-aspx-markup.md)   
 [方法: コードのローカライズ](../sharepoint/how-to-localize-code.md)   
 [方法: リソース ファイルを追加](../sharepoint/how-to-add-a-resource-file.md)   
 [方法: リソース ファイルを使用して、ローカライズされた名前、プロパティ、およびアクセス許可を指定するには](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  
  
