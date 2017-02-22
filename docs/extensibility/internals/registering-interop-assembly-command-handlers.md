---
title: "相互運用機能アセンブリ コマンド ハンドラーを登録します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "相互運用機能アセンブリ、コマンド ハンドラー"
  - "コマンドの登録の相互運用機能アセンブリの処理"
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
caps.latest.revision: 19
caps.handback.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
---
# 相互運用機能アセンブリ コマンド ハンドラーを登録します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

VSPackage に登録する必要があります [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 統合開発環境 \(IDE\) は、そのコマンドを正しくルーティングされるようにします。  
  
 手動で編集するか、レジストラー \(.rgs\) ファイルを使用して、レジストリを更新できます。 詳細については、「[レジストラー スクリプトの作成](/visual-cpp/atl/creating-registrar-scripts)」を参照してください。  
  
 管理されているパッケージ フレームワーク \(MPF\) は、この機能によって、 <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> クラスです。  
  
 [Command Table Format Reference](http://msdn.microsoft.com/ja-jp/09e9c6ef-9863-48de-9483-d45b7b7c798f) リソースは、アンマネージ サテライト UI の dll に配置されます。  
  
## VSPackage のコマンド ハンドラーの登録  
 ユーザー インターフェイス \(UI\) のハンドラーとして機能する VSPackage\-ベースのコマンドには、VSPackage にちなんだ名前のレジストリ エントリが必要です。 `GUID`します。 このレジストリ エントリでは、VSPackage の UI のリソース ファイルとそのファイル内のメニュー リソースの場所を指定します。 レジストリ エントリ自体が HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\ 下にある*\< バージョン \>*\\Menus、ここで *\< バージョン \>* のバージョンは、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], 、たとえば 9.0 です。  
  
> [!NOTE]
>  HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\ のルート パス*\< バージョン \>* 代替で上書きすることができますルートときに、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] シェルを初期化します。 ルート パスの詳細については、次を参照してください。 [Windows インストーラーである Vspackage をインストールします。](../../extensibility/internals/installing-vspackages-with-windows-installer.md)します。  
  
### CTMENU リソースのレジストリ エントリ  
 レジストリ エントリの構造です。  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\ Menus\ <GUID> = <Resource Information>  
```  
  
 \<*GUID*\> は、 `GUID` フォーム {XXXXXX\-XXXX\-XXXX\-XXXX\-XXXXXXXXX} VSPackage のです。  
  
 *\< リソース情報 \>* コンマで区切られた 3 つの要素で構成されます。 これらの要素は、注文には。  
  
 \<*リソース DLL へのパス*\>、\<*メニュー リソース ID*\>、\<*\] メニューの \[バージョン*\>  
  
 次の表のフィールドの説明 \<*リソース情報*\> です。  
  
|要素|説明|  
|--------|--------|  
|\<*リソース DLL へのパス*\>|これは、リソース、メニュー リソースを含んでいる DLL への完全パスまたは省略すると、ある VSPackage のリソース DLL を使用することを示す \(VSPackage 自体が登録されているパッケージのサブキーの説明に従って\)。<br /><br /> このフィールドは空白になります。|  
|\<*メニュー リソース ID*\>|これは、リソース ID、 `CTMENU` からコンパイルされるので、VSPackage のすべての UI 要素が含まれるリソース、 [.vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) ファイルです。|  
|\<*\] メニューの \[バージョン*\>|これは、バージョンとして使用する番号、 `CTMENU` リソースです。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] この値を使用して、確認の内容を再マージに必要なかどうか、 `CTMENU` すべてのキャッシュを持つリソース `CTMENU` リソースです。 Devenv のセットアップのコマンドを実行してトリガーを再マージされます。<br /><br /> この値は最初に 1 に設定で変更のたびにインクリメントされます、 `CTMENU` リソースを再マージが発生する前に、します。|  
  
### 例  
 リソースのエントリをいくつかの例を次に示します。  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\ Menus\ {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10 {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## 参照  
 [Vspackage でのユーザー インターフェイス要素を追加する方法](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [コマンドと相互運用機能アセンブリを使用してメニュー](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)