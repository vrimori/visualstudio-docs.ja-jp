---
title: "SccAddFromScc 関数 | Microsoft Docs"
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
  - "SccAddFromScc"
helpviewer_keywords: 
  - "SccAddFromScc 関数"
ms.assetid: 902e764d-200e-46e1-8c42-4da7b037f9a0
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# SccAddFromScc 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、ソース管理システムに既に存在するファイルを参照することができ、後でこれらのファイル部分を現在のプロジェクトを作成します。 たとえば、この関数は、ファイルをコピーせず、現在のプロジェクトに共通のヘッダー ファイルを取得できます。 ファイルの戻り値の配列 `lplpFileNames`, 、ユーザーが、IDE プロジェクトを追加するファイルの一覧が含まれています。  
  
## 構文  
  
```cpp#  
SCCRTN SccAddFromScc (  
   LPVOID   pvContext,  
   HWND     hWnd,  
   LPLONG   lpnFiles,  
   LPCSTR** lplpFileNames  
);  
```  
  
#### パラメーター  
 pvContext  
 \[in\]ソース管理プラグイン コンテキスト構造体。  
  
 hwnd の分離  
 \[in\]ソース管理プラグインは、それによって提供されるダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 lpnFiles  
 \[入力、出力\]追加されているファイルの数をバッファー。 \(これは、 `NULL` によって、メモリを指している場合 `lplpFileNames` が解放されます。 詳細については「解説」を参照します。\)  
  
 lplpFileNames  
 \[入力、出力\]ディレクトリ パスがないすべてのファイル名へのポインターの配列。 この配列が割り当てられているされ、ソース管理プラグインによって解放されます。 場合 `lpnFiles` \= 1 と `lplpFileNames` は `NULL`, 、配列の最初の名前を指す `lplpFileNames` コピー先のフォルダーが含まれています。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|ファイルが正常にあり、プロジェクトに追加。|  
|SCC\_I\_OPERATIONCANCELED|効果なしで操作が取り消されました。|  
|SCC\_I\_RELOADFILE|ファイルまたはプロジェクトを再読み込みする必要があります。|  
  
## 解説  
 IDE では、この関数を呼び出します。 ソース管理プラグインでは、ローカルの格納先フォルダーの指定をサポートする場合に、IDE が合格 `lpnFiles` \= 1 とにローカル フォルダーの名前を渡します `lplpFileNames`します。  
  
 ときにへの呼び出し、 `SccAddFromScc` 関数から返された、プラグインが割り当てられている値を `lpnFiles` と `lplpFileNames`, 、必要に応じて、ファイル名の配列のメモリを割り当て \(この割り当てには、ポインターが置き換えられます `lplpFileNames`\)。 ソース管理プラグインは、ユーザーのディレクトリに、または指定された指定のフォルダーには、すべてのファイルを配置することをします。 IDE のプロジェクトにし、ファイルが追加されます。  
  
 最後に、IDE この関数に渡すこと、もう一度 `NULL` の `lpnFiles`です。 これは、ソース管理にファイル名の配列に割り当てられたメモリを解放するプラグインによって特別なシグナルとして解釈されます。 `lplpFileNames``.`  
  
 `lplpFileNames` `char ***` ポインター。 ソース管理プラグインでは、ファイル名、つまり標準の方法でこの API の一覧を渡すことへのポインターの配列へのポインターを配置します。  
  
> [!NOTE]
>  VSSCI API の最初のバージョンは、ターゲットのプロジェクトに追加されたファイルを指定する手段を提供しませんでした。 これのセマンティクスに合わせて、 `lplpFIleNames` パラメーターが出力パラメーターではなく、入力\/出力パラメーターに強化されました。 1 つのファイルを指定すると、だけの場合は、値が指す `lpnFiles` \= 1 では、最初の要素の `lplpFileNames` ターゲット フォルダーが含まれています。 これらの新しいセマンティクスを IDE の呼び出しを使用する、 `SccSetOption` 関数を `nOption`パラメーターを設定する `SCC_OPT_SHARESUBPROJ`です。 返すかどうか、ソース管理プラグインをサポートしていないセマンティクス `SCC_E_OPTNOTSUPPORTED`します。 使用は無効を行って、 **\[ソース管理から追加** 機能します。 プラグインのサポートしている場合、 **\[ソース管理から追加** 機能 \(`SCC_CAP_ADDFROMSCC`\)、それは新しいセマンティクスをサポートありを返す必要があります `SCC_I_SHARESUBPROJOK`します。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)