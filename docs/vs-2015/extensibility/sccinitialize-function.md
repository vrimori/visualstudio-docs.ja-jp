---
title: SccInitialize 関数 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 51a908fa9ae644294567436120e8765025aba889
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537242"
---
# <a name="sccinitialize-function"></a>SccInitialize 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[SccInitialize 関数](https://docs.microsoft.com/visualstudio/extensibility/sccinitialize-function)します。  
  
この関数は、ソース管理プラグインを初期化し、機能と統合開発環境 (IDE) に制限を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
SCCRTN SccInitialize (  
   LPVOID* ppvContext,  
   HWND    hWnd,  
   LPCSTR  lpCallerName,  
   LPSTR   lpSccName,  
   LPLONG  lpSccCaps,  
   LPSTR   lpAuxPathLabel,  
   LPLONG  pnCheckoutCommentLen,  
   LPLONG  pnCommentLen  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppvContext`  
 [in]ソース管理プラグインは、ここでそのコンテキストの構造体へのポインターを配置できます。  
  
 `hWnd`  
 [in]ソース管理プラグインが提供される任意のダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 `lpCallerName`  
 [in]ソース管理プラグインを呼び出し元のプログラムの名前。  
  
 `lpSccName`  
 [入力、出力]ソース管理プラグインが独自の名前を格納するバッファー (超えない`SCC_NAME_LEN`)。  
  
 `lpSccCaps`  
 [out]ソース管理プラグインの機能フラグを返します。  
  
 `lpAuxPathLabel`  
 [入力、出力]ソース管理プラグインが説明する文字列を格納するバッファー、`lpAuxProjPath`パラメーターによって返される、 [SccOpenProject](../extensibility/sccopenproject-function.md)と[SccGetProjPath](../extensibility/sccgetprojpath-function.md) (超えない`SCC_AUXLABEL_LEN`)。  
  
 `pnCheckoutCommentLen`  
 [out]チェック アウト コメントの最大許容長を返します。  
  
 `pnCommentLen`  
 [out]その他のコメントの最大許容長を返します。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|ソース コントロールの初期化に成功しました。|  
|SCC_E_INITIALIZEFAILED|システムを初期化できませんでした。|  
|SCC_E_NOTAUTHORIZED|指定された操作を実行できません。|  
|SCC_E_NONSPECFICERROR|不特定のエラーです。ソース管理システムは初期化されませんでした。|  
  
## <a name="remarks"></a>Remarks  
 IDE は、ソース管理プラグインが初めて読み込まれるときに、この関数を呼び出します。 プラグインに、呼び出し元の名前など、特定の情報を渡す IDE できます。 IDE のコメントと機能、プラグインの許容される最大長などの特定の情報も取得バックアップします。  
  
 `ppvContext`を指す、`NULL`ポインター。 ソース管理プラグインが構造体を使用して独自の割り当てし、その構造内にポインターを格納`ppvContext`します。 IDE はこのにポインターを渡す他のすべての VSSCI API 関数、プラグインとプラグインの複数のインスタンスをサポートするためにグローバル ストレージを使用しなくても利用可能なコンテキスト情報を指定することができます。 ときにこの構造体を解放する必要があります、 [SccUninitialize](../extensibility/sccuninitialize-function.md)が呼び出されます。  
  
 `lpCallerName`と`lpSccName`パラメーター名を交換するには、IDE とソース管理プラグインを有効にします。 これらの名前は、複数のインスタンスを区別するためだけに使用可能性がありますか、メニューまたはダイアログ ボックスに実際に表示することがあります。  
  
 `lpAuxPathLabel`パラメーターは、ソリューション ファイルに格納されているプラグインへの呼び出しで、ソース コントロールに渡されるを補助プロジェクト パスを識別するために、コメントとして使用する文字列、 [SccOpenProject](../extensibility/sccopenproject-function.md)します。 [!INCLUDE[vsvss](../includes/vsvss-md.md)] 文字列を使用して"SourceSafe プロジェクト:";その他のソース管理プラグインは、この特定の文字列を使用して控える必要があります。  
  
 `lpSccCaps`パラメーターは、ソース管理プラグインのプラグインの機能を示すビットフラグを格納する場所。 (機能ビットフラグの完全な一覧を参照してください。[機能フラグ](../extensibility/capability-flags.md))。 たとえば、SCC_CAP_TEXTOUT ビット プラグインは、機能の設定、呼び出し元が提供のコールバック関数に結果を記述するプラグインのプランのかどうか。 バージョン コントロールの結果のウィンドウを作成する IDE この通知はします。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [機能フラグ](../extensibility/capability-flags.md)

