---
title: SccGet 関数 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ebda8f3e5b92089900bf8ce2d41b7d5046533895
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636756"
---
# <a name="sccget-function"></a>SccGet 関数
この関数は、表示して、コンパイルの編集ではなく、1 つまたは複数のファイルのコピーを取得します。 ほとんどのシステムでは、ファイルが読み取り専用としてタグ付けされます。  
  
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
  
### <a name="parameters"></a>パラメーター  
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
>  `SCC_GET_RECURSIVE` せずに渡す必要がありますは決して`SCC_GET_ALL`します。 また、その場合に注意してくださいディレクトリ*C:\A*と*C:\A\B*を再帰的な get に渡された両方*C:\A\B*され、すべてのサブディレクトリが 2 回取得実際にします。 IDE の必要があります: プラグインのソースではなくを制御し、配列から重複ように格納されているかどうかを確認します。  
  
 最後に、場合でも、ソース管理プラグインが指定された、`SCC_CAP_GET_NOUI`の初期化、Get コマンドのユーザー インターフェイスがないことは、この関数は、ファイルを取得する IDE によって呼び出される可能性もことを示すフラグ。 フラグは、単に、IDE で get-item メニューが表示されない、任意の UI を提供する予定のプラグインではないことを意味します。  
  
## <a name="rename-files-and-sccget"></a>ファイルと SccGet の名前を変更します。  
 状況: ユーザー ファイルをチェック アウト、たとえば、 *a.txt*、し、それを変更します。 前に*a.txt*にチェックインできる、2 番目のユーザーの名前を変更*a.txt*に*b.txt:* ソース管理データベース、チェック アウト*b.txt:* は、いくつかの変更をファイルにファイルを確認します。 最初のユーザーのローカル バージョンの名前を変更するために、2 番目のユーザーによって行われた変更は、最初のユーザーが*a.txt*ファイルを*b.txt:* と、ファイルを取得します。 最初のバージョンがまだバージョン番号を追跡するローカル キャッシュと思われるただし、 *a.txt*ローカルに格納されているため、ソース管理の相違点を解決できません。  
  
 このソース コントロールのバージョンのローカル キャッシュに、ソース管理データベースと同期されなくなるような状況を解決するのには 2 つの方法はあります。  
  
1.  現在チェック アウトされているソース管理データベースにファイル名の変更を許可しません。  
  
2.  "削除の古い"後に「新規追加」と同等の操作を行います。 次のアルゴリズムは、これを実現する 1 つの方法です。  
  
    1.  呼び出す、 [SccQueryChanges](../extensibility/sccquerychanges-function.md)関数の名前の変更の詳細について*a.txt*に*b.txt:* ソース管理データベースにします。  
  
    2.  ローカルの名前を変更*a.txt*に*b.txt:* します。  
  
    3.  呼び出す、`SccGet`両方の関数*a.txt*と*b.txt:* します。  
  
    4.  *A.txt*が存在しない、不足しているのバージョンのローカル キャッシュを消去、ソース管理データベースに*a.txt*バージョン情報。  
  
    5.  *B.txt:* チェック アウトされているファイルがローカルの内容とマージされる*b.txt:* ファイル。  
  
    6.  更新された*b.txt:* ファイル チェックするようになりましたことができます。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md)
