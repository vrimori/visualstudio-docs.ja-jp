---
title: SccGet 関数 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eb6f5204b1605969a37fd6528dda0ccaa7b8fe7f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175202"
---
# <a name="sccget-function"></a>SccGet 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この関数は、表示して、コンパイルの編集ではなく、1 つまたは複数のファイルのコピーを取得します。 ほとんどのシステムでは、ファイルが読み取り専用としてタグ付けされます。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in]ソース管理プラグインのコンテキストの構造体。  
  
 hWnd  
 [in]ソース管理プラグインが提供される任意のダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 nFiles  
 [in]指定されたファイルの数、`lpFileNames`配列。  
  
 lpFileNames  
 [in]取得するファイルの完全修飾名の配列。  
  
 方法は限られて  
 [in]コマンドのフラグ (`SCC_GET_ALL`、 `SCC_GET_RECURSIVE`)。  
  
 pvOptions  
 [in]ソース管理プラグインに固有のオプション。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|取得操作の成功します。|  
|SCC_E_FILENOTCONTROLLED|ファイルはソース管理されません。|  
|SCC_E_OPNOTSUPPORTED|ソース管理システムでは、この操作はサポートしません。|  
|SCC_E_FILEISCHECKEDOUT|ユーザーがチェック アウトして現在のファイルを取得できません。|  
|SCC_E_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題の可能性へのアクセスに問題が発生しました。 再試行をお勧めします。|  
|SCC_E_NOSPECIFIEDVERSION|無効なバージョンまたは日付/時刻が指定されました。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。ファイルは同期されませんでした。|  
|SCC_I_OPERATIONCANCELED|操作が完了する前に取り消されました。|  
|SCC_E_NOTAUTHORIZED|ユーザーは、この操作を実行する権限がありません。|  
  
## <a name="remarks"></a>Remarks  
 この関数は、数を取得するファイルの名前の配列と呼びます。 IDE は、フラグを渡す場合`SCC_GET_ALL`、つまり内の項目`lpFileNames`ファイルはなく、ディレクトリ、および取得する特定のディレクトリにソース管理下にあるすべてのファイルがあります。  
  
 `SCC_GET_ALL`フラグと組み合わせることができます、`SCC_GET_RECURSIVE`フラグを指定したディレクトリ内のすべてのファイルとすべてのサブディレクトリも取得します。  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE` せずに渡す必要がありますは決して`SCC_GET_ALL`します。 また、ディレクトリ C:\A および C:\A\B が再帰的に渡された両方の取得が場合 C:\A\B とすべてのサブディレクトリは実際に取得すること 2 回に注意してください。 IDE の必要があります: プラグインのソースではなくを制御し、配列から重複ように格納されているかどうかを確認します。  
  
 最後に、場合でも、ソース管理プラグインが指定された、`SCC_CAP_GET_NOUI`の初期化、Get コマンドのユーザー インターフェイスがないことは、この関数は、ファイルを取得する IDE によって呼び出される可能性もことを示すフラグ。 フラグは、単に、IDE で get-item メニューが表示されない、任意の UI を提供する予定のプラグインではないことを意味します。  
  
## <a name="renaming-and-sccget"></a>名前が変更され SccGet  
 状況: ユーザーは、たとえば、a.txt は、ファイルをチェック アウトし、それを変更します。 A.txt はチェックインできます、前に 2 番目のユーザー a.txt のソース管理データベースで b.txt:」に名前を変更、チェック アウト b.txt:、いくつかの変更をファイルには、し、ファイルを確認します。 最初のユーザーには、最初のユーザーは、「b.txt:」に a.txt ファイルのローカル バージョン名前を変更し、、ファイルに対する get はためにに、2 番目のユーザーによって行われた変更が希望しています。 ただし、バージョン番号を追跡するローカルのキャッシュでもと認識 a.txt の最初のバージョンがローカルに保存され、ソース管理での相違点を解決できないようにします。  
  
 このソース コントロールのバージョンのローカル キャッシュに、ソース管理データベースと同期されなくなるような状況を解決するのには 2 つの方法はあります。  
  
1.  現在チェック アウトされているソース管理データベースにファイル名の変更を許可しません。  
  
2.  "削除の古い"後に「新規追加」と同等の操作を行います。 次のアルゴリズムは、これを実現する 1 つの方法です。  
  
    1.  呼び出す、 [SccQueryChanges](../extensibility/sccquerychanges-function.md)関数をソース管理データベースで b.txt:」に a.txt の名前の変更について説明します。  
  
    2.  ローカルの a.txt の「b.txt:」名前を変更します。  
  
    3.  呼び出す、 `SccGet` a.txt と b.txt: の両方の関数。  
  
    4.  A.txt がソース管理データベースに存在しないので、不足している a.txt バージョン情報のローカル バージョンのキャッシュが削除されます。  
  
    5.  B.txt: ファイルをチェック アウトされているが、ローカル b.txt: ファイルの内容と結合されます。  
  
    6.  更新された b.txt: ファイルをチェックインにようになりましたことができます。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md)

