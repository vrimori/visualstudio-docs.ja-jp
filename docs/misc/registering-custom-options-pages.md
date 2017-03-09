---
title: "カスタム オプション ページの登録 | Microsoft Docs"
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
  - "登録、カスタムの [ツール] メニューの [オプション] ページ"
  - "[ツール] メニューの [オプション] ページ [Visual Studio SDK]、登録"
ms.assetid: 0ac6377d-a679-4f7d-be80-451c829b56f2
caps.latest.revision: 28
caps.handback.revision: 28
manager: "douge"
---
# カスタム オプション ページの登録
ユーザーおよびオートメーションをサポートするには、使用できる **ツール オプション** ページに [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の統合開発環境 \(IDE\) と適切に登録する必要があります。  
  
 マネージ パッケージのフレームワークに基づく**ツール オプション** ページには、ページを提供する VSPackage への <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> のインスタンスを適用して登録されます。  オートメーションのサポートは `true`に <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A> のプロパティの設定によって示されます。  
  
## ツールのオプション ページの登録  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の **ツール オプション** のカスタム ページを統合すると、次の場所のレジストリ エントリを作成する必要があります: *\<バージョン\>* が [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]のバージョンのです。 HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio \\*\<バージョン\>*\\ToolsOptionsPages、たとえば 8.0。  
  
 エントリに **ツール オプション** のページのカテゴリ （`<PageCategory>`）の主キー、およびページのサブ カテゴリ （`<PageSubCategory>`）の名前を含むサブキーがあります。  
  
 たとえば、文字列、 **TextEditor.Basic**で識別される **ツール オプション** のページに \=Basic `<PageSubCategory>`のサブキーのレジストリ キーの `<PageCategory>`の \=textEditor があります。  
  
 レジストリ エントリの構造は次のようにあります:  
  
 HKLM \\Software\\Microsoft\\VisualStudio \\*\<バージョン\>*\\ToolsOptionsPages \\  
  
 `<PageCategory>` \= '\#12345'  
  
 パッケージ \= " {} "  
  
 ResourcePackage \= " {YYYYYY YYYY YYYY YYYY YYYYYYYYY} "  
  
 HKLM \\Software\\Microsoft\\VisualStudio \\*\<バージョン\>*\\ToolsOptionsPages \\`<PageCategory>`  
  
 `<PageSubCategory>>` \= '\#67890'  
  
 ページ \= " {ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ} "  
  
 パッケージ \= " {AAAAAA AAAA AAAA AAAA AAAAAAAAA} "  
  
 ResourcePackage \= " {BBBBBB BBBB BBBB BBBB BBBBBBBBB} "  
  
 NoShowAllView \= 0\/1  
  
 次の表は、 HKLM \\Software\\Microsoft\\VisualStudio \\*\<バージョン\>*\\ToolsOptionsPages \\`<PageCategory>`の下に値を示します。  
  
|名前|種類|Data|Description|  
|--------|--------|----------|-----------------|  
|\(既定値\)|REG\_SZ|**ツール オプション** のカスタム ページの標準のカテゴリ名|キー名、 `<PageCategory>`は、 **ツール オプション** のページの標準の非ローカライズされたカテゴリ名です。 **Note:**  オートメーションがサポートされている場合 **ツール オプション** のページの <xref:EnvDTE.Properties> の収集を取得するには、標準の非ローカライズされたカテゴリとサブ カテゴリ名が使用されます。  詳細については、「[\[オプション\] ページの使用](../Topic/Using%20Options%20Pages.md)」を参照してください。 <br /><br /> マネージ パッケージのフレームワークに基づいて実装する際に `<PageCategory`の \> は `categoryName` の引数から <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> のコンストラクターに派生します。<br /><br /> キーが空であったり、実装のサテライト DLL でローカライズされた文字列に参照 ID を含めることができます。<br /><br /> マネージ パッケージのフレームワークに基づいて実装する際にこの値は `categoryResourceID` の引数から <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> のコンストラクターに派生します。|  
|Package|REG\_SZ|GUID|**ツール オプション** のカスタム ページを実行する VSPackage の GUID。<br /><br /> この値を取得するに <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> の使用のリフレクションを使用してマネージ パッケージのフレームワークに基づく実装。|  
|ResourcePackage|REG\_SZ|GUID|省略可能です。<br /><br /> 実行の VSPackage でそれらを指定するローカライズされた文字列を含むサテライト DLL。<br /><br /> マネージ パッケージのフレームワークは正しいリソースのパッケージを取得するためにリフレクションを使用して、 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> は、この引数を設定しません。|  
  
 次の表は、 HKLM \\Software\\Microsoft\\VisualStudio \\*\<バージョン\>*\\ToolsOptionsPages \\ \\`<PageCategory>``<PageSubCategory>`の下に値を示します。  
  
|名前|種類|Data|Description|  
|--------|--------|----------|-----------------|  
|\(既定値\)|REG\_SZ|**ツール オプション** のカスタム ページの標準のサブ カテゴリの名前|キー名、 `<PageSubCategory`の \> は、 **ツール オプション** のページのサブ カテゴリの標準の、ローカライズされていない名前です。 **Note:**  オートメーションがサポートされている場合 **ツール オプション** のページの <xref:EnvDTE.Properties> の収集を取得するには、標準の非ローカライズされたカテゴリとサブ カテゴリ名が使用されます。  詳細については、「[\[オプション\] ページの使用](../Topic/Using%20Options%20Pages.md)」を参照してください。 <br /><br /> マネージ パッケージのフレームワークに基づいて実装する際に `<PageSubegory`の \> は `pageName` の引数から <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> のコンストラクターに派生します。<br /><br /> キーが空であったり、実装のサテライト DLL でローカライズされた文字列に参照 ID を含めることができます。<br /><br /> マネージ パッケージのフレームワークに基づいて実装する際にこの値は `pageNameResourceID` の引数から <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> のコンストラクターに派生します。|  
|ページ|REG\_SZ|GUID|**ツール オプション** のカスタム ページを実行するオブジェクトの GUID。<br /><br /> <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> を使用してマネージ パッケージのフレームワークに基づく実装は、この値を取得するには、 VSPackage の <xref:System.Type> およびリフレクションを含むコンストラクターの `pageType` の引数を使用します。|  
|Package|REG\_SZ|GUID|この値を取得するに <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> の使用のリフレクションを使用してマネージ パッケージのフレームワークに基づく実装。|  
|ResourcePackage|REG\_SZ|GUID|省略可能です。<br /><br /> 実行の VSPackage でそれらを指定するローカライズされた文字列を含むサテライト DLL。<br /><br /> マネージ パッケージのフレームワークは正しいリソース DLL を取得するためにリフレクションを使用して、 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> は、この引数を設定しません。|  
|NoShowAllView|REG\_DWORD|0 または 1|省略可能です。<br /><br /> **ツール オプション** の特定のページが **ツール オプション** のページの複雑な （既定の）ビューに表示されるかどうかを示します。  オプションの特殊な簡易ビューをユーザーに提供するために共通の設定を集計する **ツール オプション** の特別なページがあるプログラミング環境を、 Visual Basic のようなサポートします。<br /><br /> REG\_DWORD エントリがゼロ以外の場合は、 **ツール オプション** のページは複雑なビューに表示されません。<br /><br /> 詳細については、「[\[オプション\] ダイアログ ボックス](../Topic/Options%20Dialog%20Box%20\(Visual%20Studio\).md)」を参照してください。<br /><br /> マネージ パッケージのフレームワークに基づく実装は、 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> のコンストラクターの `true` へ <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.NoShowAllView%2A> のプロパティを設定することにより、この値を設定できます。|  
  
 単一の相互運用機能アセンブリに基づいて VSPackage またはオブジェクトは **ツール オプション** の複数のページを実行する場合があります。  各実装が HKLM \\Software\\Microsoft\\VisualStudio \\*\<バージョン\>*\\ToolsOptionsPages の新しいエントリを必要とします。  
  
 マネージ パッケージ フレームワークが提供するオブジェクトを **ツール オプション** ページのインスタンスを作成するため、各ページは、自身を実装するオブジェクト、 VSPackage の <xref:Microsoft.VisualStudio.Shell.Package>の実装から依存しないが必要です。  
  
## オートメーションのサポート  
 **ツール オプション** のページを実行すると、オートメーションのサポートが使用されている場合は、オートメーション プロバイダーに登録する必要があります。  オートメーション プロパティを管理に使用し、 **ツール オプション** のページの状態、それを `AutomationProperty` のプロバイダーとして保存するには、永続性の機能を使用するように登録する必要があります。  
  
### オートメーション プロバイダーとして VSPackage を登録します （相互運用機能アセンブリに基づいてツールのオプション ページに対してのみ）  
 相互運用機能アセンブリに基づいて**ツール オプション** のページには、 VSPackage の実装クラスの一部として実行されます。  
  
 この場合 **ツール オプション** のページがオートメーションをサポートする場合、相互運用機能アセンブリ ベースの VSPackage は、オートメーション プロバイダーとして登録する必要があります。  
  
> [!NOTE]
>  マネージ パッケージ フレームワークのオートメーションのサポートは、 VSPackage の実装のオブジェクトの依存せずによって提供されます。  そのオブジェクトがサポートのオートメーションが、これ <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> のコンストラクターの <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A> のプロパティを使用して登録されます。  
  
 オートメーション プロバイダーとして VSPackage を登録するためのエントリは、 HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio \\*\<バージョン\>*\\Packages \\*\<PackageGUID\>*\\Automation *\<バージョン\>* が （8.0）などの [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のバージョンであり、ここで、です *\<PackageGUID\>* はオートメーション オブジェクトを実装する VSPackage の GUID です。  
  
> [!NOTE]
>  HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio \\*\<バージョン\>* のルート パスは代替のルートと Visual Studio シェルが初期化されるときにオーバーライドできます。  詳細については、「[コマンド ライン スイッチ](../extensibility/command-line-switches-visual-studio-sdk.md)」を参照してください。  
  
 レジストリ エントリの構造は次のとおりです:  
  
 HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio \\*\<バージョン\>*\\Packages \\*\<PackageGUID\>*\\Automation  
  
 `<AutomationObjectName>`  
  
|名前|種類|Data|Description|  
|--------|--------|----------|-----------------|  
|\[オートメーション\]|REG\_SZ|定義なし|未定義。<br /><br /> このキーの存在は、 *\<PackageGUID\>* によって参照される VSPackage がオートメーションをサポートすることを示します。<br /><br /> フィールドがドキュメントを格納するために使用できます。<br /><br /> <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute> は自動的にマネージ パッケージのフレームワークに基づいてアプリケーションのこのキーを作成します。|  
|`<AutomationObjectName>`|REG\_SZ|提供されるオートメーション オブジェクトの標準名|キー名のみ適用されます。  これは、オートメーション操作で使用されます。<br /><br /> フィールドがドキュメントを格納するために使用できます。<br /><br /> マネージ パッケージのフレームワークに基づいて実装する際にこのキーの名前は <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute> のコンストラクターへの `name` の引数によって決まります。<br /><br /> <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute> のコンストラクターは <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute.Description%2A> のプロパティに指定されている有効な文字列の場合、この値は、挿入されます。|  
  
### オートメーションのサポートとしてツールのオプション ページを登録します。  
 **ツール オプション** オートメーションのページへのアクセスを許可するように **ツール オプション** のページの両方のマネージ パッケージ フレームワークと相互運用機能アセンブリ ベースの実装を登録する必要があります。  これは <xref:EnvDTE>によってページへのオートメーション プロパティの永続性機能とアクセスが含まれます。  これは、オートメーション サービス プロバイダーとして VSPackage の登録に依存しない自体です。  
  
 前述したように **ツール オプション** のページの登録とエントリに **ツール オプション** のページのカテゴリ （`<PageCategory>`）の主キー、およびページのサブ カテゴリ （`<PageSubcategory>`）の名前を含むサブキーがあります。  
  
 マネージ パッケージ フレームワークを使用している場合は、クラスを `true` へ **ツール オプション** のページを登録し、ページがオートメーションをサポートすることを示すために <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A> のプロパティを設定する <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> を提供することとして使用します。  
  
 レジストリ エントリは HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio \\*\<バージョン\>*\\AutomationProperties に *\<バージョン\>* が [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]のバージョンである場合に、たとえば 8.0 です。  
  
> [!NOTE]
>  HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio \\*\<バージョン\>* のルート パスは代替のルートと Visual Studio シェルが初期化されると、詳細については、 " " を参照 [コマンド ライン スイッチ](../extensibility/command-line-switches-visual-studio-sdk.md)とオーバーライドできます。  
  
 レジストリ エントリの構造は次のようにあります:  
  
 HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio \\*\<バージョン\>\\*AutomationProperties  
  
 `<PageCategory>` \= ‘\#456’  
  
 ResourcePackage \= " {} "  
  
 `<PageSubCategory>` \= ‘\#789’  
  
 パッケージ \= " {YYYYYY YYYY YYYY YYYY YYYYYYYYY} "  
  
 名前 \= "`<PageCategory>` 。`<PageSubcategory>`"  
  
 " ProfileSave \= 1\/0  
  
 次の表は、 HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio \\*\<バージョン\>*\\AutomationProperties \\`<PageCategory>`の下に値を示します。  
  
|名前|種類|Data|Description|  
|--------|--------|----------|-----------------|  
|\(既定値\)|REG\_SZ|**ツール オプション** のカスタム ページの標準のカテゴリ名|キー名、 `<PageCategory`の \> は、 **ツール オプション** のページのカテゴリの標準の、ローカライズされていない名前です。 **Note:**  オートメーションがサポートされている場合 **ツール オプション** のページの <xref:EnvDTE.Properties> の収集を取得するには、標準の非ローカライズされたカテゴリとサブ カテゴリ名が使用されます。  詳細については、「[\[オプション\] ページの使用](../Topic/Using%20Options%20Pages.md)」を参照してください。 <br /><br /> キーが空であったり、実装のサテライト DLL でローカライズされた文字列に参照 ID を含めることができます。<br /><br /> マネージ パッケージのフレームワークに基づいて実装する際に `<PageCategory`の \> は `categoryName` の引数から <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> のコンストラクターに派生します。|  
|ResourcePackage|REG\_SZ|GUID|省略可能です。<br /><br /> 実行の VSPackage でそれらを指定するローカライズされた文字列を含むサテライト DLL。<br /><br /> マネージ パッケージのフレームワークは正しい VSPackage リソースを取得するためにリフレクションを使用して、 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> は、この引数を設定しません。|  
  
 次の表は、 HKEY\_LOCAL\_MACHINE \\SOFTWARE\\Microsoft\\VisualStudio \\*\<バージョン\>*\\AutomationProperties \\`<PageCategory>\<PageSubCategory>`の下に値を示します。  
  
|名前|種類|Data|Description|  
|--------|--------|----------|-----------------|  
|\(既定値\)|REG\_SZ|**ツール オプション** のカスタム ページのサブ カテゴリの名前|キー名、 `<PageSubCategory`の \> は、 **ツール オプション** のページのサブ カテゴリの標準の、ローカライズされていない名前です。 **Note:**  オートメーションがサポートされている場合 **ツール オプション** のページの <xref:EnvDTE.Properties> の収集を取得するには、標準の非ローカライズされたカテゴリとサブ カテゴリ名が使用されます。  詳細については、「[\[オプション\] ページの使用](../Topic/Using%20Options%20Pages.md)」を参照してください。 <br /><br /> キーが空であったり、実装のサテライト DLL でローカライズされた文字列に参照 ID を含めることができます。<br /><br /> マネージ パッケージのフレームワークに基づいて実装する際に `<PageSubCategory>` は `pageName` の引数から <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> のコンストラクターに派生します。|  
|Package|REG\_SZ|GUID|**ツール オプション** のカスタム ページを実行する VSPackage の GUID。<br /><br /> この値を取得するに <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> の使用のリフレクションを使用してマネージ パッケージのフレームワークに基づく実装。|  
|名前|REG\_SZ|**ツール オプション** のページ プロパティのコレクションの名前|**ツール オプション** のページを参照するために使用される `<PageCategory>.<PageSubCategory>` の文字列。  詳細については、「[\[オプション\] ページの使用](../Topic/Using%20Options%20Pages.md)」を参照してください。<br /><br /> マネージ パッケージのフレームワークに基づいて実装の名前は、引数から <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> のコンストラクターに派生し、フォーム `categoryName.pageName`です。|  
|ProfileSave|DWORD|1\/0|省略可能です。<br /><br /> この値は、ユーザーが **ツール\(&&T\),ツール** の **インポートとエクスポート** メニューのコマンドをクリックすると **ツール オプション** のページ設定が [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の設定の機能によって格納されるかどうかを示します。<br /><br /> キーがあり、その値が 1 の場合、 **ツール オプション** のページ構成はサポートを要求します。<br /><br /> マネージ パッケージのフレームワークに基づく実装は、 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> のコンストラクターが `true`に <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> のプロパティ設定を持っている場合はこの値を設定します。|  
  
## 参照  
 [レジストラー スクリプトの作成](/visual-cpp/atl/creating-registrar-scripts)   
 [\[オプション\] ページの使用](../Topic/Using%20Options%20Pages.md)   
 [相互運用機能アセンブリを使用した \[オプション\] ページの作成](../Topic/Creating%20Options%20Pages%20By%20Using%20Interop%20Assemblies.md)   
 [How to: Create Custom Options Pages](../Topic/How%20to:%20Create%20Custom%20Options%20Pages.md)   
 [\[オプション\] ページ](../Topic/Options%20Pages.md)   
 [オートメーション \[オプション\] ページのサポート](../Topic/Automation%20Support%20for%20Options%20Pages.md)