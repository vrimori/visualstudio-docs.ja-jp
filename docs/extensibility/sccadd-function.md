---
title: "SccAdd 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccAdd
helpviewer_keywords: SccAdd function
ms.assetid: 545268f3-8e83-446a-a398-1a9db9e866e8
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c8cd55986d7f4597030830906485ba1d7c1b3389
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="sccadd-function"></a>SccAdd 関数
この関数は、ソース管理システムに新しいファイルを追加します。  
  
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
  
#### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 hWnd  
 [in]ソース管理プラグインで提供されるダイアログ ボックスをすべての親として使用できる IDE ウィンドウへのハンドル。  
  
 nFiles  
 [in]指定されている現在のプロジェクトに追加する選択したファイルの数、`lpFileNames`配列。  
  
 lpFileNames  
 [in]追加するファイルの完全修飾のローカル名の配列。  
  
 lpComment  
 [in]追加されているファイルのすべてに適用するコメント。  
  
 pfOptions  
 [in]ファイルごとに提供されるコマンド フラグの配列です。  
  
 pvOptions  
 [in]ソース管理プラグインに固有のオプションです。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|値|説明|  
|-----------|-----------------|  
|SCC_OK|追加操作が正常に完了しました。|  
|SCC_E_FILEALREADYEXISTS|選択したファイルは、既にソース管理下にあるいます。|  
|SCC_E_TYPENOTSUPPORTED|ソース管理システムでは、(たとえば、バイナリ) ファイルの種類はサポートされていません。|  
|SCC_E_OPNOTSUPPORTED|ソース管理システムでは、この操作はサポートしません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークや競合の問題の可能性があるためのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC_E_NOTAUTHORIZED|この操作を実行するユーザーが許可されていません。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。追加は実行されません。|  
|SCC_I_OPERATIONCANCELED|操作が完了する前に取り消されました。|  
|SCC_I_RELOADFILE|ファイルまたはプロジェクトは、再読み込みする必要があります。|  
|SCC_E_FILENOTEXIST|ローカル ファイルが見つかりませんでした。|  
  
## <a name="remarks"></a>コメント  
 通常の`fOptions`配列では、ここで置換された`pfOptions`、いずれかで`LONG`ファイルあたりの仕様のオプションです。 これはため、ファイルの種類はファイルから別のファイルで異なる場合があります。  
  
> [!NOTE]
>  両方を指定することはできません`SCC_FILETYPE_TEXT`と`SCC_FILETYPE_BINARY`が、同じファイルのオプションはどちらも指定します。 どちらの設定は、設定と同じ`SCC_FILETYPE_AUTO`ソースがプラグイン初回ファイルの種類を制御する場合。  
  
 以下で使用されているフラグの一覧を示します、`pfOptions`配列。  
  
|オプション|値|説明|  
|------------|-----------|-------------|  
|SCC_FILETYPE_AUTO|0x00|ソース管理プラグインは、ファイルの種類を検出する必要があります。|  
|SCC_FILETYPE_TEXT|0x01|ASCII テキスト ファイルを示します。|  
|SCC_FILETYPE_BINARY|0x02|ASCII テキスト以外のファイルの種類を示します。|  
|SCC_ADD_STORELATEST|0x04|デルタ ファイルの最新のコピーだけを格納しません。|  
|SCC_FILETYPE_TEXT_ANSI|0x08|ANSI テキストとしてファイルを処理します。|  
|SCC_FILETYPE_UTF8|0x10|UTF8 形式の Unicode テキストとしてファイルを処理します。|  
|SCC_FILETYPE_UTF16LE|0x20|UTF16 で Unicode テキストとしてリトル エンディアン形式のファイルを処理します。|  
|SCC_FILETYPE_UTF16BE|0x40|UTF16 ビッグ エンディアン Unicode テキストとしてファイル形式を扱います。|  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)