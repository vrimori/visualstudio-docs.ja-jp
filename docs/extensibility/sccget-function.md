---
title: "SccGet 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccGet
helpviewer_keywords: SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 73f5c55b39d855eb084206ef27e2254d50377b86
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sccget-function"></a>SccGet 関数
この関数は、1 つまたは複数のファイルを表示およびコンパイルするためはなく、編集、コピーを取得します。 ほとんどのシステムでは、ファイルが読み取り専用としてタグ付けされます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccGet(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]ソース管理プラグインの context 構造体。  
  
 hWnd  
 [in]ソース管理プラグインで提供されるダイアログ ボックスをすべての親として使用できる IDE ウィンドウへのハンドル。  
  
 nFiles  
 [in]指定されたファイルの数、`lpFileNames`配列。  
  
 lpFileNames  
 [in]取得するファイルの完全修飾名の配列。  
  
 foptions の   
 [in]コマンドのフラグ (`SCC_GET_ALL`、 `SCC_GET_RECURSIVE`)。  
  
 pvOptions  
 [in]ソース管理プラグインに固有のオプションです。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|取得操作が成功します。|  
|SCC_E_FILENOTCONTROLLED|ファイルはソース管理されません。|  
|SCC_E_OPNOTSUPPORTED|ソース管理システムでは、この操作はサポートしません。|  
|SCC_E_FILEISCHECKEDOUT|ユーザーがチェック アウトして現在のファイルを取得できません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークや競合の問題の可能性があるためのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC_E_NOSPECIFIEDVERSION|無効なバージョンまたは日付/時刻を指定します。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。ファイルは同期されませんでした。|  
|SCC_I_OPERATIONCANCELED|操作が完了する前に取り消されました。|  
|SCC_E_NOTAUTHORIZED|ユーザーは、この操作を実行する権限がありません。|  
  
## <a name="remarks"></a>コメント  
 この関数は、カウントを取得するファイルの名前の配列と呼びます。 IDE は、フラグを渡す場合`SCC_GET_ALL`、つまり、内の項目に`lpFileNames`ファイルはなく、ディレクトリ、および指定したディレクトリ内のソース管理下にあるすべてのファイルを取得します。  
  
 `SCC_GET_ALL`フラグと組み合わせることができます、`SCC_GET_RECURSIVE`フラグを指定したディレクトリ内のすべてのファイルと同様のすべてのサブディレクトリを取得します。  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE`せずに渡す必要がありますは決して`SCC_GET_ALL`です。 また、C:\A および C:\A\B ディレクトリが再帰的に渡された両方の取得が場合 C:\A\B とそのすべてのサブディレクトリが実際に取得すること 2 回に注意してください。 IDE の責任 — およびプラグインのソースではなくが制御 — 配列外このなどの重複部分を保持することを確認します。  
  
 最後に、場合でも、ソース管理プラグインが指定された、`SCC_CAP_GET_NOUI`の初期化、Get コマンドのユーザー インターフェイスがない、この関数は、ファイルを取得する IDE によっても呼び出されることを示すフラグ。 フラグは、こと、IDE で Get メニュー項目が表示されませんし、UI を提供する予定のプラグインがないことを意味します。  
  
## <a name="renaming-and-sccget"></a>名前が変更され SccGet  
 状況: ユーザーは、たとえばの a.txt ファイルをチェック アウトし、それを変更します。 A.txt をチェックインすることができます、前に 2 番目のユーザー a.txt をソース管理データベースに b.txt:」に名前を変更、チェック アウト b.txt:、ファイルにいくつかの変更は、およびファイルをチェックインします。 最初のユーザーには、最初のユーザーが「b.txt:」に a.txt ファイルのローカル バージョン名前を変更し、、ファイルの取得には、2 番目のユーザーによって行われた変更が希望していますいます。 ただし、バージョン番号を追跡するローカル キャッシュもと認識 a.txt の最初のバージョンがローカルに格納されているし、ソース管理で相違点を解決できないためです。  
  
 これにはソース コントロールのバージョンのローカル キャッシュがソース管理データベースとの同期にこのような状況を解決するのには 2 つの方法があります。  
  
1.  現在チェック アウトされているソース管理データベースにファイル名の変更を許可しません。  
  
2.  "Delete 古い"後「新規追加」と同等の操作を行います。 次のアルゴリズムは、これを実現する 1 つの方法です。  
  
    1.  呼び出す、 [SccQueryChanges](../extensibility/sccquerychanges-function.md)関数の詳細については、ソース管理データベースに b.txt:」に a.txt の名前を変更します。  
  
    2.  ローカルの a.txt の「b.txt:」名前を変更します。  
  
    3.  呼び出す、 `SccGet` a.txt と b.txt: の両方の関数。  
  
    4.  A.txt がソース管理データベースに存在しないために、不足している a.txt バージョン情報のローカル バージョンのキャッシュが削除されます。  
  
    5.  チェック アウトされている b.txt: ファイルは、ローカル b.txt: ファイルの内容に結合されます。  
  
    6.  更新された b.txt: ファイルをチェックインにようになりましたことができます。  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md)