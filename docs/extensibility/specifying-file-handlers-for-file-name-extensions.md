---
title: "ファイル名拡張子のファイルのハンドラーを指定する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: file extensions, specifying file handlers
ms.assetid: e3de4730-a95c-465a-b3b2-92ca85364ad7
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d5db7a218a718e27f584abbf350b49907b56fb17
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-file-handlers-for-file-name-extensions"></a>ファイル名拡張子のファイルのハンドラーを指定します。
特定のファイル拡張子を持つファイルを処理するアプリケーションを判断する方法の数があります。 OpenWithList と OpenWithProgids 動詞とは、ファイルのファイル拡張子のレジストリ エントリのハンドラーを指定する方法は 2 つです。  
  
## <a name="openwithlist-verb"></a>OpenWithList 動詞  
 Windows エクスプ ローラーでファイルを右クリックすると表示、**開く**コマンド。 複数の製品は、拡張機能に関連付けられて、表示、**ファイルを開く**サブメニュー。  
  
 HKEY_CLASSES_ROOT でファイル拡張子に対する OpenWithList キーを設定して拡張機能を開くにはさまざまなアプリケーションを登録することができます。 下にあるこのキー ファイルの拡張子の下に記載されているアプリケーションが表示される、**推奨されたプログラム**の見出し、**ファイルを開く** ダイアログ ボックス。 次の例を開くには、ファイル拡張子は .vcproj 登録されたアプリケーションを示します。  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithList\  
         devenv.exe  
```  
  
> [!NOTE]
>  アプリケーションを指定するキーは HKEY_CLASSES_ROOT\Applications 下の一覧です。  
  
 OpenWithList キーを追加すると、別のアプリケーション拡張機能の所有権を取得する場合でも、アプリケーションがファイル拡張子をサポートしているを宣言します。 アプリケーションまたは別のアプリケーションの将来のバージョンが考えられます。  
  
## <a name="openwithprogids"></a>OpenWithProgIDs  
 プログラム id (Progid) とは、Classid、アプリケーションまたは COM オブジェクトのバージョンを識別するわかりやすいバージョンです。 すべての共同作成可能なオブジェクトは、独自の ProgID が必要です。 たとえば、VisualStudio.DTE.7.1 は Visual Studio .NET 2003 を起動の VisualStudio.DTE.10.0 の起動中に[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 プロジェクトの種類またはプロジェクト項目の種類の所有者では、ファイル拡張機能のバージョンに固有の ProgID を作成する必要があります。 Progid としては、1 つ以上の ProgID 可能性があります、同じアプリケーションを開始点で冗長な可能性があります。 詳細については、次を参照してください。[動詞ファイル名拡張子を登録する](../extensibility/registering-verbs-for-file-name-extensions.md)です。  
  
 バージョン管理されたファイルの Progid の他のベンダーからの登録の重複を避けるために次の命名規則を使用します。  
  
|ファイル拡張子|バージョン管理された ProgID|  
|--------------------|----------------------|  
|*.extension|ProductName です。 extension.versionMajor.versionMinor|  
  
 バージョン管理された Progid を値として、HKEY_CLASSES_ROOT に追加する特定のファイル拡張子を開くことができるさまざまなアプリケーションを登録する\\*\<拡張子 >*\OpenWithProgids キー。 このレジストリ キーには、ファイル拡張子に関連付けられている代替 Progid の一覧が含まれています。 表示された Progid に関連付けられているアプリケーションに表示されます、**ファイルを開く***Product Name*サブメニュー。 両方で同じアプリケーションが指定されている場合、`OpenWithList`と`OpenWithProgids`キー、オペレーティング システムが、重複部分を結合します。  
  
> [!NOTE]
>  `OpenWithProgids`キーは Windows XP でのみサポートされます。 他のオペレーティング システムは、このキーを無視する、ためにをファイル ハンドラーの唯一の登録と使用しないでです。 このキーを使用して、Windows XP のユーザー エクスペリエンスが向上します。  
  
 REG_NONE 型の値として、目的の Progid を追加します。 次のコードは、ファイル拡張子の Progid を登録する次の例を示します (.*ext*)。  
  
```  
HKEY_CLASSES_ROOT\  
   .ext\  
      (default)="MyProduct.ext.14.0"  
      OpenWithProgids  
         progid        REG_NONE (zero-length binary value)  
         otherprogid   REG_NONE (zero-length binary value)  
```  
  
 ファイル拡張子に対する既定値は既定のファイル ハンドラーとして指定された ProgID です。 以前のバージョンに付属するファイル拡張子の ProgID を変更する場合[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]または他のアプリケーションを引き継ぐすることができますし、登録する必要があります、`OpenWithProgids`ファイル拡張機能のキーし、と共に一覧で、新しい ProgID を指定サポートする古い Progid です。 例:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)="VisualStudio.vcproj.14.0"  
      OpenWithProgids  
         vcprojfile              //old progid  
         VisualStudio.vcproj.12.0 //old progid  
         VisualStudio.vcproj.14.0 //new progid  
```  
  
 かどうか、古い ProgID に関連付けられている動詞、これらの動詞は、も表示されます。**ファイルを開く** *Product Name* 、ショートカット メニュー。  
  
## <a name="see-also"></a>参照  
 [ファイル名の拡張機能の概要](../extensibility/about-file-name-extensions.md)   
 [ファイル名拡張子の動詞を登録する](../extensibility/registering-verbs-for-file-name-extensions.md)