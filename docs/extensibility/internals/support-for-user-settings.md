---
title: "ユーザー設定のサポート | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "カスタム設定のポイント"
  - "永続化のサポートを登録するユーザーの設定 [Visual Studio SDK]"
  - "永続化ストアの設定を登録します。"
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# ユーザー設定のサポート
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VSPackage でグループが、ユーザーが選択したときに永続化状態変数の 1 つまたは複数の設定カテゴリを定義できます、 **設定のインポート\/エクスポート** コマンドを **ツール** メニュー。 この永続化を有効にする設定を使用して Api で、 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]です。  
  
 カスタム設定のポイントと GUID として参照されているレジストリ エントリは、VSPackage のカテゴリの設定を定義します。 カスタム設定のポイントで定義されたを VSPackage が複数の設定のカテゴリをサポートできます。  
  
-   相互運用機能アセンブリに基づく設定の実装 \(を使用して、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> インターフェイス\)、レジストリを編集するか、レジストラー スクリプト \(.rgs ファイル\) を使用してカスタム設定のポイントを作成する必要があります。 詳細については、「[レジストラー スクリプトの作成](/visual-cpp/atl/creating-registrar-scripts)」を参照してください。  
  
-   管理されているパッケージ フレームワーク \(MPF\) を使用するコードは、アタッチすることによってカスタム設定ポイントを作成する必要があります、 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> カスタム設定の各点の VSPackage にします。  
  
     単一 VSPackage がいくつかのカスタム設定のポイントをサポートしている場合は、カスタム設定の各点が、別のクラスによって実装されるの一意のインスタンスによって登録されている各、 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> クラスです。 その結果、クラスを実装する設定は、1 つ以上のカテゴリの設定をサポートできます。  
  
## ポイントのレジストリ エントリのカスタム設定の詳細  
 カスタム設定のポイントは、次の場所にレジストリ エントリで作成されます: HKLM\\Software\\Microsoft\\VisualStudio\\*\< バージョン \>*\\UserSettings\\`<CSPName>`, ここで、 `<CSPName>` 、VSPackage がサポートするカスタム設定のポイントの名前と *\< バージョン \>* のバージョンは、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], 、8.0 などです。  
  
> [!NOTE]
>  HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\ のルート パス*\< バージョン \>* 代替でオーバーライドできるルートときに、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 統合開発環境 \(IDE\) を初期化します。 詳細については、「[コマンド ライン スイッチ](../../extensibility/command-line-switches-visual-studio-sdk.md)」を参照してください。  
  
 レジストリ エントリの構造は、次に示します。  
  
 HKLM\\Software\\Microsoft\\VisualStudio\\*\< バージョン \>*\\UserSettings\\  
  
 `<CSPName`\> \= '\#12345' s  
  
 パッケージ ' {XXXXXX XXXX XXXX XXXX XXXXXXXXX}' を \=  
  
 カテゴリ \= ' {YYYYYY YYYY YYYY YYYY YYYYYYYYY}'  
  
 ResourcePackage \= ' {ZZZZZZ"zzzz"ZZZZ"zzzz"ZZZZZZZZZ}'  
  
 AlternateParent \= \[区分名\]  
  
|名前|型|データ|説明|  
|--------|-------|---------|--------|  
|\(既定\)|REG\_SZ|カスタム設定のポイントの名前|キーの名前、 `<CSPName`\>、カスタム設定のポイントのローカライズされていない名前を指定します。<br /><br /> 結合することで取得 MPF に基づいた実装例、キーの名前、 `categoryName` と `objectName` の引数、 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> コンス トラクターに `categoryName_objectName`します。<br /><br /> キーは空であることができますか、サテライト DLL にローカライズされた文字列への参照 ID を含めることができます。 この値を取得してから、 `objectNameResourceID` への引数、 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> コンス トラクターです。|  
|パッケージ|REG\_SZ|GUID|カスタム設定のポイントを実装する VSPackage の GUID です。<br /><br /> 実装が使用し MPF に基づいて、 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> クラスでコンス トラクターの使用を `objectType` 、VSPackage を含む引数 <xref:System.Type> し、この値を取得するためにリフレクションします。|  
|カテゴリ|REG\_SZ|GUID|カテゴリの設定を識別する GUID。<br /><br /> この値は任意に選択した、相互運用機能アセンブリに基づいた実装では、GUID を [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE に渡します、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> と <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> メソッドです。 これら 2 つのメソッドのすべての実装では、その GUID 引数を確認してください。<br /><br /> MPF に基づいた実装例、この GUID を取得して、 <xref:System.Type> 実装するクラスの [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] メカニズムを設定します。|  
|ResourcePackage|REG\_SZ|GUID|省略可能です。<br /><br /> サテライト DLL を含むへのパスは、実装の VSPackage がそれらを指定しない場合、文字列がローカライズされます。<br /><br /> MPF リフレクションを使用して、適切なリソース、VSPackage を取得するため、 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> クラスは、この引数を設定しません。|  
|AlternateParent|REG\_SZ|このカスタム設定のポイントを含むツール オプション ページの下のフォルダーの名前です。|省略可能です。<br /><br /> 設定の実装がサポートしている場合にのみ、この値を設定する必要があります **ツール オプション** で永続化メカニズムを使用しているページ、 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 状態を保存するオートメーション モデルのメカニズムではなく。<br /><br /> AlternateParent キーの値は、このような場合、 `topic` のセクションで、 `topic.sub-topic` 特定を識別するために使用される文字列 **ツールオプション** ページです。 たとえば、 **ツールオプション** ページ `"TextEditor.Basic"` AlternateParent の値になります `"TextEditor"`します。<br /><br /> ときに <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 、カスタム設定のポイントを生成カテゴリ名と同じです。|