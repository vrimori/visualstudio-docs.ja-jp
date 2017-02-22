---
title: "SccGet 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccGet"
helpviewer_keywords: 
  - "SccGet 関数"
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# SccGet 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、1 つまたは複数のファイルを表示して、コンパイルするだけのための編集のコピーを取得します。 ほとんどのシステムでは、ファイルが読み取り専用としてタグ付けされます。  
  
## 構文  
  
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
  
#### パラメーター  
 pvContext  
 \[in\]ソース管理プラグインの context 構造体。  
  
 hwnd の分離  
 \[in\]ソース管理プラグインは、それによって提供されるダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 nFiles  
 \[in\]指定されたファイルの数、 `lpFileNames` 配列。  
  
 lpFileNames  
 \[in\]取得するファイルの完全修飾名の配列。  
  
 される  
 \[in\]コマンドのフラグ \(`SCC_GET_ALL`, 、`SCC_GET_RECURSIVE`\)。  
  
 pvOptions  
 \[in\]ソース管理プラグインに固有のオプションです。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|Get 操作が成功します。|  
|SCC\_E\_FILENOTCONTROLLED|ファイルはソース管理されていません。|  
|SCC\_E\_OPNOTSUPPORTED|ソース管理システムでは、この操作はサポートされません。|  
|SCC\_E\_FILEISCHECKEDOUT|ユーザーがチェック アウトして現在のファイルを取得できません。|  
|SCC\_E\_ACCESSFAILURE|ソース管理システムのネットワークまたは競合の問題が原因と思わのアクセスに関する問題が発生しました。 再試行することをお勧めします。|  
|SCC\_E\_NOSPECIFIEDVERSION|無効なバージョンまたは日付\/時刻を指定します。|  
|SCC\_E\_NONSPECIFICERROR|不特定のエラーです。ファイルは同期されませんでした。|  
|SCC\_I\_OPERATIONCANCELED|操作が完了する前に取り消されました。|  
|SCC\_E\_NOTAUTHORIZED|ユーザーは、この操作を実行する権限がありません。|  
  
## 解説  
 この関数は、カウントを取得するファイルの名前の配列で呼び出されます。 IDE は、フラグを渡す場合 `SCC_GET_ALL`, 、つまり内の項目 `lpFileNames` はなく、ファイルが、ディレクトリを取得する指定されたディレクトリでソース管理下にあるすべてのファイルがあるとします。  
  
 `SCC_GET_ALL` フラグと組み合わせることができます、 `SCC_GET_RECURSIVE` フラグを指定したディレクトリ内のすべてのファイルと同様に、すべてのサブディレクトリを取得します。  
  
> [!NOTE]
>  `SCC_GET_RECURSIVE` せずに渡す必要があるは決して `SCC_GET_ALL`します。 また、C:\\A および C:\\A\\B ディレクトリが取得再帰的に渡される両方の場合 C:\\A\\B とそのすべてのサブディレクトリは実際に取得すること 2 回に注意してください。 IDE の役目です: プラグインのソースではなくを制御し、配列から重複が次のように格納されているかどうかを確認します。  
  
 最後に、ソース管理プラグイン場合でも指定されている、 `SCC_CAP_GET_NOUI` の初期化、Get コマンドのユーザー インターフェイスがないことは、この関数は、ファイルを取得する IDE によっても呼び出されますことを示すフラグ。 フラグは、IDE で Get メニュー項目が表示されない、UI を提供する必要は、プラグインがないことを意味します。  
  
## 名前を変更して SccGet  
 状況: ユーザーなどの a.txt ファイルをチェック アウトし、それを変更します。 チェックイン a.txt を前に 2 番目のユーザー a.txt をソース管理データベースに b.txt:」に名前を変更、b.txt: チェック\_アウト、いくつかの変更、ファイルには、およびファイルをチェックインします。 最初のユーザーには、最初のユーザーが「b.txt:」に a.txt ファイルのローカル バージョン名前を変更し、、ファイルに対して get をは、2 番目のユーザー行った変更が希望しています。 ただし、バージョン番号を追跡するローカル キャッシュもと認識 a.txt の最初のバージョンがローカルに格納されているし、ソース管理での相違点を解決できないようにします。  
  
 ソース コントロールのバージョンのローカルのキャッシュがソース管理データベースとの同期になったこの状況を解決するのには 2 つの方法があります。  
  
1.  現在チェック アウトされているソース管理データベース内のファイルの名前を変更することはできません。  
  
2.  "削除の古い"後に「新規追加」と同等の操作を行います。 次のアルゴリズムは、これを実現する 1 つの方法です。  
  
    1.  呼び出す、 [SccQueryChanges](../extensibility/sccquerychanges-function.md) 関数をソース管理データベースに b.txt:」に a.txt の名前の変更について説明します。  
  
    2.  ローカルの a.txt の「b.txt:」名前を変更します。  
  
    3.  呼び出す、 `SccGet` a.txt と b.txt: の両方の関数です。  
  
    4.  A.txt がソース管理データベースに存在しないために、不足している a.txt バージョン情報のローカル バージョンのキャッシュが消去されます。  
  
    5.  チェック アウトされている b.txt: ファイルは、ローカル b.txt: ファイルの内容に結合されます。  
  
    6.  更新された b.txt: ファイル今すぐチェックインすることができます。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md)