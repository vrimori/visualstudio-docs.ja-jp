---
title: SccAdd 関数 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccAdd
helpviewer_keywords:
- SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5124088599eced9d5ae6bc17365d06dc36f81987
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027894"
---
# <a name="sccadd-function"></a>SccAdd 関数
この関数では、ソース管理システムに新しいファイルを追加します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccAdd(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG*     pfOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 hWnd  
 [in]ソース管理プラグインが提供される任意のダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 nFiles  
 [in]指定されている現在のプロジェクトに追加する選択したファイルの数、`lpFileNames`配列。  
  
 lpFileNames  
 [in]追加するファイルの完全修飾のローカル名の配列。  
  
 lpComment  
 [in]追加されるファイルのすべてに適用されるコメントです。  
  
 pfOptions  
 [in]ファイル単位で提供される、コマンド フラグの配列。  
  
 pvOptions  
 [in]ソース管理プラグインに固有のオプション。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|追加操作が正常に完了しました。|  
|SCC_E_FILEALREADYEXISTS|選択したファイルは、既にソース管理下にあるいます。|  
|SCC_E_TYPENOTSUPPORTED|(たとえば、バイナリ) ファイルの種類は、ソース管理システムでサポートされていません。|  
|SCC_E_OPNOTSUPPORTED|ソース管理システムでは、この操作はサポートしません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題の可能性へのアクセスに問題が発生しました。 再試行をお勧めします。|  
|SCC_E_NOTAUTHORIZED|この操作を実行できません。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。追加は実行されません。|  
|SCC_I_OPERATIONCANCELED|操作が完了する前に取り消されました。|  
|SCC_I_RELOADFILE|ファイルまたはプロジェクトを再読み込みする必要があります。|  
|SCC_E_FILENOTEXIST|ローカル ファイルが見つかりませんでした。|  
  
## <a name="remarks"></a>Remarks  
 通常の`fOptions`、配列では、ここが置き換えられます`pfOptions`、いずれかで`LONG`仕様ファイルごとのオプションします。 これはため、ファイルの種類がファイルをファイルに異なる場合があります。  
  
> [!NOTE]
>  両方とも指定することはできません`SCC_FILETYPE_TEXT`と`SCC_FILETYPE_BINARY`が同じファイルのオプションはいずれも指定するは無効です。 設定と同じでは、どちらも設定`SCC_FILETYPE_AUTO`ソースがプラグインの初回ファイルの種類を制御する場合。  
  
 使用されているフラグの一覧を次に示します、`pfOptions`配列。  
  
|オプション|[値]|説明|  
|------------|-----------|-------------|  
|SCC_FILETYPE_AUTO|0x00|ソース管理プラグインは、ファイルの種類を検出する必要があります。|  
|SCC_FILETYPE_TEXT|0x01|ASCII テキスト ファイルを示します。|  
|SCC_FILETYPE_BINARY|0x02|ASCII テキスト以外のファイルの種類を示します。|  
|SCC_ADD_STORELATEST|0x04|デルタ ファイルの最新のコピーだけを格納しません。|  
|SCC_FILETYPE_TEXT_ANSI|0x08|ANSI テキストとしてファイルを扱います。|  
|SCC_FILETYPE_UTF8|0x10|UTF8 形式での Unicode テキストとしてファイルを扱います。|  
|SCC_FILETYPE_UTF16LE|0x20|UTF16 に Unicode テキストとしてリトル エンディアン形式のファイルを扱います。|  
|SCC_FILETYPE_UTF16BE|0x40|UTF16 ビッグ エンディアン Unicode テキストとしてファイル形式を扱います。|  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)