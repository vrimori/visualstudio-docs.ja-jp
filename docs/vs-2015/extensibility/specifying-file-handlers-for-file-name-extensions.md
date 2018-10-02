---
title: ファイル名拡張子のファイル ハンドラーを指定する |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 83bbc57098a68239a1ef26548e9cf05fd31322bb
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2018
ms.locfileid: "47592695"
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>ファイル名拡張子のファイル ハンドラーを指定する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ファイル名拡張子のファイル ハンドラーを指定する](https://docs.microsoft.com/visualstudio/extensibility/specifying-file-handlers-for-file-name-extensions)します。  
  
特定のファイル拡張子を持つファイルを処理するアプリケーションを判断する方法を数多くあります。 OpenWithList と OpenWithProgids 動詞は、ファイル拡張子のレジストリ エントリのファイル ハンドラーを指定する 2 つの方法です。  
  
## <a name="openwithlist-verb"></a>OpenWithList 動詞  
 Windows エクスプ ローラーでファイルを右クリックすると表示、**オープン**コマンド。 1 つ以上の製品は、拡張機能に関連付けられて、表示、**プログラムから開く**サブメニューで開く。  
  
 HKEY_CLASSES_ROOT で、ファイル拡張子の OpenWithList キーを設定して、拡張機能を開くにはさまざまなアプリケーションを登録することができます。 このキー ファイルの拡張機能の下に表示されているアプリケーションは、下に表示されます、**推奨プログラム**に見出し、**プログラムから開く** ダイアログ ボックス。 .Vcproj ファイルの拡張子を開くように登録するアプリケーションは、次の例です。  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
>  アプリケーションを指定するキーは HKEY_CLASSES_ROOT\Applications 下の一覧です。  
  
 OpenWithList キーを追加すると、別のアプリケーション拡張機能の所有権を取得する場合でも、アプリケーションがファイルの拡張機能をサポートしているを宣言します。 これは、アプリケーションまたは別のアプリケーションの将来のバージョン。  
  
## <a name="openwithprogids"></a>OpenWithProgIDs  
 プログラム識別子 (Progid) とは、Classid バージョンのアプリケーションや COM オブジェクトを識別するわかりやすいバージョンです。 すべての共同作成可能なオブジェクトには、独自の ProgID が必要です。 たとえば、VisualStudio.DTE.7.1 は Visual Studio .NET 2003 を開始の VisualStudio.DTE.10.0 の起動中に[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]します。 プロジェクトの種類またはプロジェクト項目の種類の所有者は、ファイル拡張機能のバージョンに固有の ProgID を作成する必要があります。 この Progid は、1 つ以上の ProgID が同じアプリケーションを開始点で冗長な可能性があります。 詳細については、次を参照してください。[ファイル名拡張子の動詞を登録する](../extensibility/registering-verbs-for-file-name-extensions.md)します。  
  
 バージョン管理されたファイルの Progid の他のベンダーからの登録での重複を避けるために、次の名前付け規則を使用します。  
  
|ファイル拡張子|バージョン管理された ProgID|  
|--------------------|----------------------|  
|.extension|ProductName します。 extension.versionMajor.versionMinor|  
  
 バージョン管理された Progid を値として、HKEY_CLASSES_ROOT に追加する特定のファイル拡張子を開くことができる別のアプリケーションを登録できる\\*\<拡張機能 >* \OpenWithProgids キー。 このレジストリ キーには、ファイル拡張子に関連付けられている代替の Progid の一覧が含まれています。 表示されている Progid に関連付けられているアプリケーションに表示されます、**プログラムから開く**_製品名_サブメニューで開く。 両方で同じアプリケーションが指定されている場合、`OpenWithList`と`OpenWithProgids`キー、オペレーティング システムは、重複をマージします。  
  
> [!NOTE]
>  `OpenWithProgids`キーは Windows XP でのみサポートされます。 他のオペレーティング システムは、このキーを無視する、ためにをハンドラーのファイルののみ登録として使用しないでください。 このキーを使用すると、Windows XP の優れたユーザー エクスペリエンスを提供できます。  
  
 REG_NONE 型の値としては、目的の Progid を追加します。 次のコードは、ファイル拡張子の Progid を登録する例を示します (.*ext*)。  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 ファイル拡張子の既定値は既定のファイル ハンドラーとして指定された ProgID です。 以前のバージョンに同梱されているファイル拡張子の ProgID を変更する場合[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]またはその他のアプリケーションでは、引き継ぐすることができますし、登録する必要があります、`OpenWithProgids`ファイル拡張機能のキーし、と共に一覧での新しい ProgID を指定します。サポートする古い Progid。 例えば:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 古い ProgID がそれに関連付けられている動詞としている場合、これらの動詞はでも表示されます**プログラムから開く***製品名*ショートカット メニュー。  
  
## <a name="see-also"></a>関連項目  
 [ファイル名拡張子について](../extensibility/about-file-name-extensions.md)   
 [ファイル名拡張子の動詞を登録する](../extensibility/registering-verbs-for-file-name-extensions.md)

