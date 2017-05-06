---
title: "SharePoint ソリューションのローカライズ"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.GlobalAndFeatureResource"
  - "VS.SharePoint.Project.AddResourceDialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "グローバライズ [Visual Studio での SharePoint 開発]"
  - "ローカライズ [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発、ローカライズ"
ms.assetid: 0d4cfa2b-8b48-45c7-bbee-ece9b0baffaf
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# SharePoint ソリューションのローカライズ
  アプリケーションを世界中で使用できるように準備するプロセスをローカライズと呼びます。  ローカライズでは、リソースを特定のカルチャに翻訳します。  詳細については、「[アプリケーションのグローバライズとローカライズ](../ide/globalizing-and-localizing-applications.md)」を参照してください。  このトピックでは、SharePoint ソリューションをローカライズする方法の概要について説明します。  
  
 ソリューションをローカライズするには、ハードコーディングされた文字列をコードから削除してリソース ファイルに抽出します。  リソース ファイルとは、.resx 拡張子を持つ [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ベースのファイルです。  リソース ファイルには、ソリューションで使用される文字列の翻訳されたバージョンが含まれています。  詳細については、「[Resources in Applications \(アプリケーションのリソース\)](http://go.microsoft.com/fwlink/?LinkID=155844)」を参照してください。  
  
> [!NOTE]  
>  SharePoint ソリューションのリソース ファイルに追加するのは文字列リソースだけです。  リソース エディターでは文字列以外のリソースも追加できますが、文字列以外のリソースは SharePoint に配置されません。  
  
## リソース ファイル  
 リソース ファイルには、既定のリソース ファイル、言語に依存しないリソース ファイル、および言語固有のリソース ファイルの 3 種類があります。  
  
|リソース ファイルの種類|説明|  
|------------------|--------|  
|既定の|フォールバック リソースとも呼ばれます。既定のリソース ファイルには、既定のカルチャ \(英語など\) にローカライズされた文字列が含まれます。  これらは、指定された言語のローカライズされたリソース ファイルが見つからない場合に使用されます。  既定のリソースは、独立したファイルを持たず、メイン アプリケーション アセンブリに格納されます。|  
|言語に依存しないリソース ファイル|特定の言語にはローカライズされているが特定のカルチャにはローカライズされていない文字列を含むリソース ファイル   \(たとえば、フランス語の場合は "fr"\)。|  
|言語固有のリソース ファイル|特定の言語とカルチャにローカライズされた文字列を含むリソース ファイル   \(たとえば、フランス語 \(カナダ\) の場合は "fr\-CA"\)。|  
  
 詳細については、「[Hierarchical Organization of Resources for Localization \(ローカライズ用リソースの階層構造\)](http://go.microsoft.com/fwlink/?LinkId=178360)」を参照してください。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で開発する SharePoint プロジェクトで既定のリソース ファイルを指定するには、リソース ファイルを追加する際、**\[リソースの追加\]** ダイアログ ボックスのカルチャの一覧で **\[ロケールに依存しない言 \(ロケールに依存しない国\)\]** を選択します。  
  
## Visual Studio SharePoint ソリューションのローカライズ  
 ソリューションをローカライズする際には、そのソリューションでユーザーに表示されるすべてのテキスト情報を考慮に入れる必要があります。  たとえば、情報メッセージ、エラー メッセージ、および [!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] 文字列を翻訳して、リソース ファイルに配置する必要があります。  
  
 リソース ファイルでは、すべての文字列に一意の識別子があります。  翻訳した文字列に対しては、各リソース ファイルで同じ識別子を使用する必要があります。  たとえば、既定のリソース ファイルの最初の文字列の識別子が "String1" だった場合は、言語固有のリソース ファイルの最初の文字列の識別子も "String1" にします。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint アプリケーションでは、フィーチャー、ASPX ページ マークアップ、およびコードの 3 つの領域をローカライズするのが一般的です。  以降の説明では、SharePoint ソリューションをドイツ語と日本語にローカライズする場合を想定しています。  既定の言語は英語です。  
  
### フィーチャーのローカライズ  
 フィーチャーをローカライズするには、ハードコーディングされたフィーチャーのタイトルと説明を、ローカライズされたリソース ファイルに含まれている翻訳済みのタイトルと文字列を参照する式に置き換える必要があります。  この変更は、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] の**フィーチャー デザイナー**で行います。  詳細については、「[方法: フィーチャーをローカライズする](../sharepoint/how-to-localize-a-feature.md)」を参照してください。  
  
 英語のフィーチャーをドイツ語と日本語にローカライズするには、プロジェクトに 3 つのリソース ファイル プロジェクト項目 \(英語用、ドイツ語用、および日本語用\) を追加します。  フィーチャー リソース ファイルは、ASPX マークアップやコードのローカライズには使用できません。これらにはまた別のリソース ファイルが必要です。  
  
 フィーチャー リソース ファイルを作成したら、そこに翻訳済みの文字列を追加します。  ローカライズされた文字列にアクセスするには次の形式の式を使用します。  
  
```  
$Resources:String ID  
```  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] のフィーチャー リソースの名前は常に Resources です。  ロケールに依存しない言語以外を選択した場合、リソース ファイル名にカルチャ [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] が追加されます。  たとえば、ロケールに依存しない言語 \(既定\) のフィーチャー リソース ファイルを追加した場合は、 Resources.resx となります。  日本語 \(日本\) のカルチャを選択して言語固有のフィーチャー リソースを追加した場合は名前が Resources.ja\-JP.resx になります。  フィーチャー リソース ファイルの名前は自動的に割り当てられ、変更することはできません。  
  
 フィーチャー リソースのスコープは、追加先のフィーチャーのローカル スコープです。  ソリューション内の任意のフィーチャー ファイルや要素ファイルで使用できるリソースを作成するには、フィーチャー リソース ファイルではなく **\[グローバル リソース ファイル\]** プロジェクト項目を追加します。  **\[グローバル リソース ファイル\]** プロジェクト項目は、**\[新しい項目の追加\]** ダイアログ ボックスの **\[SharePoint\]** の下の **\[2010\]** フォルダーにあります。  グローバル リソース ファイルは、SharePoint ルート フォルダーの \\Resources フォルダーに配置されます。  
  
### ASPX ページ マークアップのローカライズ  
 [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] のページをローカライズするには、3 つのリソース ファイル プロジェクト項目 \(英語用、ドイツ語用、日本語用\) を追加します。  マークアップに加えてコードをローカライズする必要がない場合は、代わりにグローバル リソース ファイルを追加できます。  
  
 既定の言語のリソース ファイルに任意の名前を付けます。  ローカライズされたリソース ファイルに対しては、同じ名前に言語固有のカルチャ [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] を加えた名前を使用します   \(ドイツ語の場合は MyAppResources.de\-DE.resx、日本語の場合は MyAppResources.ja\-JP.resx など\)。  
  
 各リソース ファイルの **\[配置タイプ\]** プロパティを **\[AppGlobalResource\]** に設定します。  これにより、リソース ファイルが App\_GlobalResources フォルダーに配置されます。このフォルダーに配置されたリソース ファイルは、ソリューション内のすべての ASPX ページと ASPX コントロールで使用できます。  App\_GlobalResources フォルダーは、C:\\inetpub\\wwwroot\\wss\\VirtualDirectories\\\<ポート番号\>\\App\_GlobalResources にあります。  
  
> [!NOTE]  
>  グローバルではないリソース ファイルを使用する場合は、それらをプロジェクト項目フォルダーに移動します。これにより、\[配置タイプ\] プロパティやその他の SharePoint 固有のプロパティを使用できるようになります。  
  
 ASPX マークアップ リソース ファイルは、コードのローカライズにも使用できます。  リソースを ASPX マークアップだけでなくコードのローカライズにも使用する場合は、各ファイルの \[ビルド アクション\] プロパティの設定を \[埋め込まれたリソース\] のままにして、リソースがサテライト アセンブリにコンパイルされるようにします。  リソース ファイルをマークアップのローカライズのみに使用する場合は、\[ビルド アクション\] プロパティを \[コンテンツ\] に変更して、ファイルがメイン アプリケーション アセンブリにコンパイルされないようにすることもできます。  
  
 ASPX ページと ASPX コントロールのマークアップで、ハードコーディングされたプロパティ文字列をすべて次の形式の式に置き換えます。  
  
```  
<asp:<class> runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 たとえば、次のようになります。  
  
```  
<asp:Button ID="btn1" runat="server" onclick="btn1_Click" Text="<%$Resources:Resource1,String7%>"></asp:Button>  
```  
  
 テキストとしての ASPX に対しては次の形式の式を使用します。  
  
```  
<asp:literal ID="<ID>" runat="server" Text="<%$Resources:<Resource File Name>, <String ID>%>" />  
```  
  
 たとえば、次のようになります。  
  
```  
<asp:literal ID="Literal1" runat="server" Text="<%$Resources:Resource1, String9%>" />  
```  
  
 詳細については、「[方法: ASPX マークアップをローカライズする](../sharepoint/how-to-localize-aspx-markup.md)」を参照してください。  
  
### コードのローカライズ  
 フィーチャーの文字列と [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] のマークアップに加えて、ソリューション コード内のメッセージ文字列やエラー文字列をローカライズする必要もあります。  ローカライズされた情報とエラー メッセージはサテライト アセンブリに格納されます。  サテライト アセンブリには、[!INCLUDE[TLA2#tla_ui](../sharepoint/includes/tla2sharptla-ui-md.md)] テキストや例外出力メッセージなど、ユーザーに表示される文字列が格納されます。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] では、.NET Framework の標準のハブ アンド スポーク モデルが使用されており、  ハブ \(メイン プログラム アセンブリ\) に既定の言語リソースが含まれ、  スポーク \(サテライト アセンブリ\) に言語固有のリソースが含まれます。  詳細については、「[リソースのパッケージ化と配置](http://go.microsoft.com/fwlink/?LinkId=179280)」を参照してください。  サテライト アセンブリはリソース \(.resx\) ファイルからコンパイルされます。  プロジェクトとソリューション パッケージに言語固有のリソース ファイルを追加すると、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] により、それらのリソース が *Project Name*.resources.dll という名前のサテライト アセンブリにコンパイルされます。  
  
 SharePoint アプリケーションのコードをローカライズするには、ASPX マークアップの場合と同様に、既定の言語用と各ローカライズ言語用の個別のリソース ファイル プロジェクト項目をプロジェクトに追加します。  ただし、前述のとおり、ASPX マークアップのローカライズ用のリソース ファイルが既にある場合は、それらをコードのローカライズに再利用できます。  リソース ファイルを作成する必要がある場合は、.resx 拡張子が付いた任意の名前を既定の言語のリソース ファイルに付けます。  ローカライズされたリソース ファイルに対しては、同じ名前に言語固有のカルチャ [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] を加えた名前を使用します。  各リソース ファイルの \[ビルド アクション\] プロパティを \[埋め込まれたリソース\] に設定して、サテライト リソース アセンブリが作成されるようにします。  
  
 サテライト アセンブリを作成するには、プロジェクトをビルドした後、**パッケージ デザイナー**の **\[詳細設定\]** タブでファイルを追加のアセンブリとして追加します。  アセンブリを追加するとき、場所を表すパスの先頭にカルチャ [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] フォルダーを付加します \(de\-DE\\*Project Item Name*.resources.dll など\)。  これにより、同じ名前の複数のファイルをパッケージに含めることができます。  
  
 コードで次の構文を使用して、ハードコーディングされた文字列を <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> メソッドの呼び出しに置き換えます。  
  
```  
HttpContext.GetGlobalResourceObject("<Resource File Name>", "<String ID>")  
```  
  
 詳細については、「[方法: コードをローカライズする](../sharepoint/how-to-localize-code.md)」を参照してください。  
  
#### Web パーツ コードのローカライズ  
 Web パーツに含まれるカスタム プロパティ エディター機能には、ハードコーディングされた文字列を使用するコード属性 \(WebDisplayName、Category、WebDescription など\) が含まれています。  これらの属性の文字列値を置き換えるには、属性のクラスから派生する別のクラスを作成して、  それらのクラスで属性のプロパティを設定します。  属性のプロパティは基底クラスに依存します。  たとえば、WebDisplayName 属性のプロパティは DisplayNameValue で、WebDescription 属性のプロパティは DescriptionValue です。  
  
 派生クラスで、リソース ファイルの文字列 ID と ResourceManager オブジェクトを参照してその文字列 ID のローカライズされた値を取得し、  その値をプロパティ エディターの属性に返します。  
  
## 参照  
 [方法: フィーチャーをローカライズする](../sharepoint/how-to-localize-a-feature.md)   
 [方法: ASPX マークアップをローカライズする](../sharepoint/how-to-localize-aspx-markup.md)   
 [方法: コードをローカライズする](../sharepoint/how-to-localize-code.md)   
 [方法: リソース ファイルを追加する](../sharepoint/how-to-add-a-resource-file.md)   
 [方法: リソース ファイルを使用して、ローカライズした名前、プロパティ、およびアクセス許可を指定する](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)  
  
  