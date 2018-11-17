---
title: SccPopulateList 関数 |Microsoft Docs
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
- SccPopulateList
helpviewer_keywords:
- SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fccf5ba354a99eaef6968c5d5027e8540762af75
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798899"
---
# <a name="sccpopulatelist-function"></a>SccPopulateList 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この関数は、特定のソース制御コマンドのファイルの一覧を更新し、指定されたすべてのファイルをソース管理の状態を提供します。  
  
## <a name="syntax"></a>構文  
  
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
  
#### <a name="parameters"></a>パラメーター  
 pvContext  
 [in]ソース管理プラグイン コンテキスト構造体。  
  
 %n されたコマンド  
 [in]ソース管理のコマンドですべてのファイルに適用される、`lpFileNames`配列 (を参照してください[コマンド コード](../extensibility/command-code-enumerator.md)可能なコマンドの一覧については)。  
  
 nFiles  
 [in]ファイルの数、`lpFileNames`配列。  
  
 lpFileNames  
 [in]IDE に既知のファイル名の配列。  
  
 pfnPopulate  
 [in]IDE のコールバック関数を追加し、ファイルを削除するために呼び出す (を参照してください[POPLISTFUNC](../extensibility/poplistfunc.md)詳細については)。  
  
 pvCallerData  
 [in]コールバック関数に渡される値は変更されません。  
  
 lpStatus  
 [入力、出力]ソース管理プラグインを各ファイルのステータスのフラグを返すの配列。  
  
 方法は限られて  
 [in]コマンドのフラグ (の「PopulateList フラグ」セクションを参照して[特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md)詳細については)。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|成功。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>Remarks  
 この関数は、現在の状態のファイルの一覧を調べます。 使用して、`pfnPopulate`ファイルでの条件が一致しない場合に、呼び出し元に通知するコールバック関数、`nCommand`します。 たとえば、次のコマンドは`SCC_COMMAND_CHECKIN`コールバックは、呼び出し元に通知するために使用し、一覧内のファイルがチェック アウトできません。 場合によっては、ソース管理プラグインはでしたコマンドの一部にして、それらを追加するその他のファイルを検索する可能性があります。 これにより、たとえば、Visual Basic のユーザーが自分のプロジェクトで使用されますが、Visual Basic のプロジェクト ファイルに表示されない .bmp ファイルをチェック アウトできます。 ユーザーが選択、**取得**IDE でコマンド。 IDE、ユーザーを取得できると思われるすべてのファイルの一覧が表示されますが、一覧が表示される前に、`SccPopulateList`関数が呼び出されて表示される一覧が最新の状態かどうかを確認します。  
  
## <a name="example"></a>例  
 IDE は、ユーザーが取得できると思われるファイルの一覧を作成します。 この一覧を表示にする前に呼び出し、 `SccPopulateList` 、関数を追加し、一覧からファイルを削除する機会に、ソース管理プラグインを提供します。 プラグインに指定したコールバック関数を呼び出すことによって、一覧を変更 (を参照してください[POPLISTFUNC](../extensibility/poplistfunc.md)の詳細)。  
  
 呼び出す、プラグインは引き続き、`pfnPopulate`関数を追加して、ファイルを削除しますが終了してから戻りますまで、`SccPopulateList`関数。 IDE では、その一覧を表示できます。 `lpStatus`配列は、IDE によって渡される元のリストのすべてのファイルを表します。 プラグインの塗りつぶしにこれらのファイルさらにすべての状態では、コールバック関数の使用します。  
  
> [!NOTE]
>  ソース管理プラグインは、常に、オプションは、リストのまま、この関数からすぐに返すことだけを持ちます。 プラグインは、この関数を実装する場合を示している可能性これを設定して、`SCC_CAP_POPULATELIST`最初の呼び出しで機能フラグ、 [SccInitialize](../extensibility/sccinitialize-function.md)します。 既定では、プラグイン、常に想定してくださいに渡されるすべての項目にファイルがあります。 ただし、IDE が設定されている場合、`SCC_PL_DIR`フラグ、`fOptions`ディレクトリと見なされるパラメーターに渡されるすべての項目が。 プラグインがディレクトリに追加の属しているすべてのファイル。 ファイルとディレクトリの組み合わせの IDE に適合ことはありません。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md)   
 [コマンド コード](../extensibility/command-code-enumerator.md)

