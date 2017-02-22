---
title: "ファイル名拡張子のファイル ハンドラーを指定します。 | Microsoft Docs"
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
  - "ファイル拡張子、ファイル ハンドラーを指定します。"
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# ファイル名拡張子のファイル ハンドラーを指定します。
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

特定のファイル拡張子を持つファイルを処理するアプリケーションを判断する方法の数があります。 OpenWithList と OpenWithProgids 動詞とは、ファイル拡張子のレジストリ エントリのファイル ハンドラーを指定する方法は 2 つです。  
  
## OpenWithList 動詞  
 Windows エクスプ ローラーでファイルを右クリックすると表示、 **開く** コマンドです。 複数の製品が拡張子が関連付けられている場合は、表示、 **ファイルを開く** サブメニュー。  
  
 HKEY\_CLASSES\_ROOT 内のファイル拡張子に対する OpenWithList キーを設定した拡張機能を開くようにするさまざまなアプリケーションを登録することができます。 このキー ファイルの拡張子の下に記載されているアプリケーションが下に表示されます、 **推奨されたプログラム** の見出し、 **ファイルを開く** \] ダイアログ ボックス。 .Vcproj ファイル拡張子を開くように登録するアプリケーションを次の例に示します。  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
>  これらは HKEY\_CLASSES\_ROOT\\Applications 下の一覧のアプリケーションを指定するキーです。  
  
 OpenWithList キーを追加することで、アプリケーションでは、別のアプリケーション拡張機能の所有権を取得する場合でも、ファイル拡張子がサポートしていることを宣言します。 アプリケーションまたは別のアプリケーションの将来のバージョンが考えられます。  
  
## OpenWithProgIDs  
 プログラム id \(Progid\) には、アプリケーションまたは COM オブジェクトのバージョンを識別する Classid のわかりやすいバージョンがあります。 すべての共同作成可能なオブジェクト固有の ProgID が必要です。 たとえば、VisualStudio.DTE.7.1 は Visual Studio .NET 2003年を起動の VisualStudio.DTE.10.0 の起動中に [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。 プロジェクトの種類またはプロジェクト項目の種類の所有者では、ファイル拡張機能のバージョンに固有の ProgID を作成する必要があります。 この Progid で 1 つ以上の ProgID がアプリケーションを起動、同じ冗長な可能性があります。 詳細については、「[ファイル名拡張子の動詞を登録します。](../extensibility/registering-verbs-for-file-name-extensions.md)」を参照してください。  
  
 その他のベンダからの登録の重複を避けるために、バージョン管理されたファイルの Progid の名前付け規則を使用します。  
  
|ファイル拡張子|バージョン管理された ProgID|  
|-------------|-----------------------|  
|.extension|ProductName します。 extension.versionMajor.versionMinor|  
  
 バージョン管理された Progid を値として、HKEY\_CLASSES\_ROOT\\ に追加する特定のファイル拡張子を開くことができるさまざまなアプリケーションを登録する*\< extension \>*\\OpenWithProgids キー。 このレジストリ キーには、ファイル拡張子に関連付けられている代替の Progid の一覧が含まれています。 表示されている Progid に関連付けられているアプリケーションに表示されます、 **ファイルを開く***製品名* サブメニュー。 両方で同じアプリケーションが指定されている場合、 `OpenWithList` と `OpenWithProgids` キー、オペレーティング システムは、重複をマージします。  
  
> [!NOTE]
>  `OpenWithProgids` キーは、Windows XP でのみサポートされます。 他のオペレーティング システムがこのキーを無視するためをファイル ハンドラーの唯一の登録として使用しないでください。 このキーを使用すると、Windows xp より優れたユーザー エクスペリエンスを提供できます。  
  
 REG\_NONE 型の値として、目的の Progid を追加します。 次のコード ファイルの拡張子を Progid を登録する例を示します \(.*ext*\).  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 ファイル拡張子の既定値は、既定のファイル ハンドラーとして指定された ProgID です。 以前のバージョンに付属するファイル拡張子の ProgID を変更する場合 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] または他のアプリケーションを引き継ぐすることができますし、登録する必要があります、 `OpenWithProgids` ファイル拡張子に対してキーをサポートする古い Progid と共に一覧で新しい ProgID を指定します。 例:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 古い ProgID は、関連付けられた動詞かどうかは、これらの動詞が表示されも **ファイルを開く** *製品名* のショートカット メニューにします。  
  
## 参照  
 [ファイル名拡張子](../extensibility/about-file-name-extensions.md)   
 [ファイル名拡張子の動詞を登録します。](../extensibility/registering-verbs-for-file-name-extensions.md)