---
title: "SccPopulateList 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccPopulateList"
helpviewer_keywords: 
  - "SccPopulateList 関数"
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# SccPopulateList 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、特定のソース管理コマンドのファイルのリストを更新し、指定されたすべてのファイルに対してソース管理ステータスを提供します。  
  
## 構文  
  
```cpp#  
SCCRTN SccPopulateList (  
   LPVOID          pvContext,  
   enum SCCCOMMAND nCommand,  
   LONG            nFiles,  
   LPCSTR*         lpFileNames,  
   POPLISTFUNC     pfnPopulate,  
   LPVOID          pvCallerData,  
   LPLONG          lpStatus,  
   LONG            fOptions  
);  
```  
  
#### パラメーター  
 pvContext  
 \[in\]ソース管理プラグイン コンテキスト構造体。  
  
 %t%7  
 \[in\]ソース管理のコマンドですべてのファイルに適用される、 `lpFileNames` 配列 \(を参照してください [コマンドのコード](../extensibility/command-code-enumerator.md) 可能なコマンドの一覧については\)。  
  
 nFiles  
 \[in\]内のファイルの数、 `lpFileNames` 配列。  
  
 lpFileNames  
 \[in\]IDE に認識されているファイルの名前の配列。  
  
 pfnPopulate  
 \[in\]IDE のコールバック関数を追加し、ファイルを削除するために呼び出す \(を参照してください [POPLISTFUNC](../extensibility/poplistfunc.md) 詳細\)。  
  
 pvCallerData  
 \[in\]コールバック関数に渡される値は変更されません。  
  
 lpStatus  
 \[入力、出力\]ソース管理を各ファイルのステータスのフラグを返すプラグインの配列。  
  
 される  
 \[in\]コマンドのフラグ \(の"PopulateList flag"を参照してください [特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md) 詳細\)。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|成功。|  
|SCC\_E\_NONSPECIFICERROR|不特定のエラーです。|  
  
## 解説  
 この関数は、現在の状態のファイルの一覧を調べます。 使用して、 `pfnPopulate` ファイルに使用される条件に一致しない場合、呼び出し元に通知するコールバック関数、 `nCommand`です。 たとえば、次のコマンドは `SCC_COMMAND_CHECKIN` リスト内のファイルがチェック アウトできませんし、呼び出し元に通知するコールバックを使用します。 場合によっては、ソース管理プラグインには、コマンドの一部である可能性があり、追加する他のファイルがあります。 これにより、たとえば、Visual Basic のユーザーが自分のプロジェクトで使用される Visual Basic プロジェクト ファイルにない .bmp ファイルをチェック アウトできます。 ユーザーが選択、 **取得** IDE でコマンドです。 IDE が発生することができますと思われるすべてのファイルの一覧を表示、ボックスの一覧を表示すると、前に、 `SccPopulateList` 関数が呼び出されて表示される一覧が最新の状態かどうかを確認します。  
  
## 例  
 IDE では、ユーザーを取得できると思われるファイルの一覧を作成します。 この一覧が表示される前に呼び出し、 `SccPopulateList` 関数を追加し、一覧からファイルを削除する機会に、ソース管理プラグインを提供します。 プラグインに指定されたコールバック関数を呼び出すことによってリストを変更 \(表示 [POPLISTFUNC](../extensibility/poplistfunc.md) 詳細については\)。  
  
 プラグインの継続を呼び出す、 `pfnPopulate` 関数が追加されから戻りますを終了するまで、ファイルが削除、 `SccPopulateList` 関数です。 IDE では、その一覧を表示できます。`lpStatus` 配列は、IDE から渡された元のリストのすべてのファイルを表します。 プラグインの塗りつぶしに取り組んでこれらのファイルさらにすべての状態では、コールバック関数の使用します。  
  
> [!NOTE]
>  ソース管理プラグインには、常に、単にすぐに、一覧のままであるため、この関数から返すようにオプションがあります。 プラグインは、この関数を実装する場合、分かりますこれを設定して、 `SCC_CAP_POPULATELIST` 機能ビットフラグ最初の呼び出しで、 [SccInitialize](../extensibility/sccinitialize-function.md)です。 既定では、プラグイン、常に想定してくださいに渡されるすべての項目にファイルがあること。 ただし、IDE を設定する場合、 `SCC_PL_DIR` フラグ、 `fOptions` パラメーターに渡されるすべての項目が見なされるディレクトリです。 プラグインに追加します属しているすべてのファイルのディレクトリ。 IDE は、ファイルとディレクトリの組み合わせで渡してください。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md)   
 [コマンドのコード](../extensibility/command-code-enumerator.md)