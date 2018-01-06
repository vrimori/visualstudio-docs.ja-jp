---
title: "SccPopulateList 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccPopulateList
helpviewer_keywords: SccPopulateList function
ms.assetid: 7416e781-c571-4a7f-8af3-a089ce8be662
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 474bb834d36661c7cd85b98db78c13f619d7cba6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sccpopulatelist-function"></a>SccPopulateList 関数
この関数は、特定のソース管理コマンドのファイルの一覧を更新し、指定されたすべてのファイルのソース管理の状態を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
  
 %t%7  
 [in]ソース管理コマンドのすべてのファイルに適用される、`lpFileNames`配列 (を参照してください[コマンド コード](../extensibility/command-code-enumerator.md)可能なコマンドの一覧については)。  
  
 nFiles  
 [in]内のファイルの数、`lpFileNames`配列。  
  
 lpFileNames  
 [in]IDE に既知のファイル名の配列。  
  
 pfnPopulate  
 [in]ファイル追加および削除するために呼び出す IDE コールバック関数 (を参照してください[POPLISTFUNC](../extensibility/poplistfunc.md)詳細)。  
  
 pvCallerData  
 [in]コールバック関数に渡される値が変更されません。  
  
 lpStatus  
 [入力、出力].ソース管理プラグインの各ファイルの状態フラグを返すの配列。  
  
 foptions の   
 [in]コマンドのフラグ (の「PopulateList フラグ」セクションを参照して[ビットフラグが特定のコマンドで使用される](../extensibility/bitflags-used-by-specific-commands.md)詳細については)。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|成功。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>コメント  
 この関数は、現在の状態のファイルの一覧を調べます。 使用して、`pfnPopulate`ファイルに使用される条件に一致しない場合、呼び出し元に通知するコールバック関数、`nCommand`です。 たとえば、次のコマンドは`SCC_COMMAND_CHECKIN`リスト内のファイルがチェック アウトされませんし、呼び出し元に通知するコールバックを使用します。 場合によっては、ソース管理プラグインはでしたコマンドの一部にして、それらを追加する他のファイルを見つける可能性があります。 これにより、たとえば、Visual Basic のユーザーが自分のプロジェクトで使用される Visual Basic プロジェクト ファイルにない .bmp ファイルをチェック アウトできます。 ユーザーが選択、**取得**IDE でコマンド。 IDE が発生することができますと思われるすべてのファイルの一覧に表示されますが、一覧が表示される前に、`SccPopulateList`関数が呼び出されて表示される一覧が最新の状態かどうかを確認します。  
  
## <a name="example"></a>例  
 IDE では、ユーザーが取得できると思われるファイルの一覧を構築します。 この一覧が表示されます、前に呼び出し、`SccPopulateList`関数は、ソース管理プラグインする機会を与える追加ファイルを一覧から削除します。 プラグインに指定されたコールバック関数を呼び出すことによって、一覧を変更 (を参照してください[POPLISTFUNC](../extensibility/poplistfunc.md)詳細)。  
  
 プラグインは引き続き呼び出し、`pfnPopulate`関数では、追加され、ファイルを削除が終了してから戻りますまで、`SccPopulateList`関数。 IDE は、その一覧を表示できます。 `lpStatus`配列は、IDE によって渡された元のリストのすべてのファイルを表します。 プラグインの塗りつぶしに取り組んでこれらのファイルまたすべての状態では、コールバック関数の使用します。  
  
> [!NOTE]
>  ソース管理プラグインでは、単にすぐには、一覧のまま、この関数から返されるオプションが常にあります。 プラグインは、この関数を実装する場合を示しますこの設定によって、`SCC_CAP_POPULATELIST`最初の呼び出しで機能フラグ、 [SccInitialize](../extensibility/sccinitialize-function.md)です。 既定では、プラグイン常に想定してくださいで渡されるすべての項目がファイルであること。 ただし、IDE 設定する場合、`SCC_PL_DIR`フラグ、`fOptions`ディレクトリと見なされるパラメーターに渡されるすべての項目はします。 プラグイン ファイルを追加するすべて、属しているディレクトリにします。 ファイルとディレクトリの組み合わせは IDE を渡すことはありません。  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)   
 [特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md)   
 [コマンドのコード](../extensibility/command-code-enumerator.md)