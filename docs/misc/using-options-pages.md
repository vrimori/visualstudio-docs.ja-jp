---
title: "[オプション] ページの使用 | Microsoft Docs"
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
  - "[ツール オプション] ページ [Visual Studio SDK]、使用法"
ms.assetid: 5ae6b995-3aeb-43a7-9786-4cf69faa101c
caps.latest.revision: 36
caps.handback.revision: 36
manager: "douge"
---
# [オプション] ページの使用
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] オートメーション モデルは、VSPackage が **\[ツール\]** メニューの **\[オプション\]** ダイアログ ボックスにアクセスできるようにする <xref:EnvDTE.DTE> オブジェクトを提供します。  
  
 通常、**\[オプション\]** ダイアログ ボックスのページが [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 統合開発環境 \(IDE\) か VSPackage によって提供されている場合は、オートメーション モデルを使用してこれらのページにアクセスできます。 ただし、次のようないくつかの例外があります。  
  
-   **\[ダイナミック ヘルプ\]** ページの設定には、プログラムでアクセスできません。**\[ダイナミック ヘルプ\]** の機能は、オートメーション モデルを使用して制御できますが、コード内で直接制御する必要があります。 詳細については、「[How to: Control the Dynamic Help Window](http://msdn.microsoft.com/ja-jp/7f5777aa-c270-4058-a175-8ce8a4ed25eb)」を参照してください。  
  
-   **\[フォントおよび色\]** ページの設定は、オートメーション モデルではなく、独自の API によって制御されます。 詳細については、「[フォントおよび色を使用します。](../extensibility/using-fonts-and-colors.md)」を参照してください。  
  
-   言語固有のプロパティは、オートメーション モデルからは取得できません。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] オートメーション モデルをサポートしない **\[オプション\]** ページは、照会されたときにオートメーション <xref:EnvDTE.Properties> コレクションを返さない場合があります。 コレクションが返される場合、一部の機能は含まれません。 これらの機能の管理方法については、「[DTE Properties Collections](../Topic/DTE%20Properties%20Collections.md)」をご覧ください。  
  
## \[オプション\] ページの管理  
 **\[オプション\]** ページを管理するには、VSPackage はオートメーション モデルから <xref:EnvDTE.DTE> オブジェクトを取得する必要があります。  
  
> [!NOTE]
>  VSPackage がオートメーション モデルを使用して、インストールされている **\[オプション\]** に対するクエリを実行し、設定を変更する場合、IDE の機能は拡張されません。 このため、このパッケージはオートメーション オブジェクトを実装する必要はありません。  
  
 <xref:EnvDTE.DTE> オブジェクトをオートメーション モデルから取得するには、次のようにして <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> メソッドを呼び出し、`SID_SDTE` のサービス ID 引数および `IID__DTE` のインターフェイス引数を指定します。  
  
```  
pServiceProvider->QueryService(SID_SDTE, IID__DTE, (LPVOID*)pDTE);  
```  
  
 <xref:EnvDTE.DTE> オブジェクトを管理パッケージ フレームワーク \(MPF\) を使用して取得するには、<xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> メソッドを呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.SDTE> 型の `serviceType` パラメーターを指定します。  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#01](../misc/codesnippet/CSharp/using-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#01](../misc/codesnippet/VisualBasic/using-options-pages_1.vb)]  
  
 **\[オプション\]** ページが 2 つの識別子で指定されています。 最初の識別子は、**\[オプション\]** ページが含まれているフォルダーを示す文字列です。 2 番目の識別子は、そのフォルダー内の特定の項目を示す文字列です。 これらは、**\[オプション\]** ページのカテゴリとサブカテゴリ、またはそのトピックとサブトピックとして参照されます。  
  
 たとえば、Basic コードを処理するテキスト エディターの設定は、**\[Text Editor\]** フォルダーの **\[Basic\]** メンバーとしてナビゲーション ウィンドウに表示されます。 カテゴリの識別子は `TextEditor`、そのサブカテゴリは `Basic` で、**\[オプション\]** ページ自体は `TextEditor.Basic` ページとして参照されます。  
  
> [!NOTE]
>  ローカライズその他の理由により、**\[オプション\]** ページに表示される名前は、カテゴリ識別子およびサブカテゴリ識別子として使用される文字列とは異なる場合があります。 正しい識別子が他のどこにも記載されていない場合、オートメーションを使用して IDE に対してクエリを実行し、正しい識別子を取得することが必要になる場合があります。 レジストリの場所は、HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<VS Version\>*\\AutomationProperties です。ここで *\<VS Version\>*は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のリリースのバージョン番号を表しています。 詳細については、「[カスタム オプション ページの登録](../misc/registering-custom-options-pages.md)」を参照してください。  
  
 次の例を使用して、オートメーション モデルから `TextEditor.Basic` ページのプロパティを取得できます。  
  
```  
CComPtr<_DTE> srpDTE; CComPtr<Properties> srpDTEPropertiesList; hr = srpDTE->get_Properties("TextEditor", "Basic", &srpDTEPropertiesList);  
```  
  
 MPF を使用してこのプロパティを取得するには、<xref:EnvDTE._DTE.Properties%2A> メソッドを使用します。  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#02](../misc/codesnippet/CSharp/using-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#02](../misc/codesnippet/VisualBasic/using-options-pages_2.vb)]  
  
 <xref:EnvDTE.Properties.Item%2A> メソッドは、<xref:EnvDTE.Properties> コレクションから個別の設定を <xref:EnvDTE.Property> オブジェクトとして返します。  
  
 カテゴリおよびサブカテゴリと同様に、各設定は一意の文字列を識別子として持っています。 たとえば、`TextEditor.Basic` ページの **\[タブ サイズ\]** 設定は、文字列 `TabSize` で識別されます。  
  
> [!NOTE]
>  ローカライズその他の理由により、**\[オプション\]** ページに表示される名前は、設定識別子として使用される文字列とは異なる場合があります。 正しい識別子が他のどこにも記載されていない場合、オートメーションを使用して IDE に対してクエリを実行し、正しい識別子を取得することが必要になる場合があります。  
  
 <xref:EnvDTE.Properties> コレクションの <xref:EnvDTE.Properties.Item%2A> メソッドによって返される <xref:EnvDTE.Property> オブジェクトの <xref:EnvDTE.Property.Value%2A> を使用して、設定状態に対してクエリを実行し変更することができます。  
  
 たとえば、`TextEditor.Basic` ページの **\[タブ サイズ\]** 設定をオートメーション モデルを使用して設定するには、次の例で返される <xref:EnvDTE.Properties> オブジェクトを使用します。  
  
```  
CComPtr<Property> srpProperty; hr = srpDTEPropertiesList->Item("TabSize", &srpProperty); hr= srpProperty.set_Value(4);  
```  
  
 次の例で、MPF を使用して **\[タブ サイズ\]** 設定を更新する方法を示します。  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#03](../misc/codesnippet/CSharp/using-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#03](../misc/codesnippet/VisualBasic/using-options-pages_3.vb)]  
  
 詳細については、「[Controlling Options Settings](../Topic/Controlling%20Options%20Settings.md)」を参照してください。  
  
## オプション ページの設定の保持  
 IDE は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] オートメーション モデルを完全にサポートする **\[オプション\]** ページの状態の永続性を実装します。  
  
 IDE に含まれているページの設定は、**\[ツール\]** メニューの **\[設定のインポート\/エクスポート\]** コマンドをユーザーがクリックすると自動的に保存 \(または取得\) されます。  
  
 `ProfileSave` フラグを HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<VS Version\>*\\AutomationProperties の下にあるカスタム **\[オプション\]** ページ レジストリ エントリに追加することにより、カスタム **\[オプション\]** ページでこの自動永続性サポートを使用できます。ここで、*\<VS Version\>* は [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のリリースのバージョン番号を表しています。 詳細については、「[カスタム オプション ページの登録](../misc/registering-custom-options-pages.md)」を参照してください。  
  
## 参照  
 [相互運用機能アセンブリを使用した \[オプション\] ページの作成](../Topic/Creating%20Options%20Pages%20By%20Using%20Interop%20Assemblies.md)   
 [\[オプション\] ページを作成します。](../Topic/Creating%20Options%20Pages.md)   
 [オートメーションを使用した \[オプション\] ページの作成](../Topic/Creating%20Options%20Pages%20By%20Using%20Automation.md)   
 [Controlling Options Settings](../Topic/Controlling%20Options%20Settings.md)   
 [カスタム オプション ページの登録](../misc/registering-custom-options-pages.md)   
 [オプション ページを開く](../misc/opening-an-options-page.md)   
 [ユーザー設定の拡張とオプション](../extensibility/extending-user-settings-and-options.md)