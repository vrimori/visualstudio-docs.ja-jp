---
title: "SccInitialize 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccInitialize"
helpviewer_keywords: 
  - "SccInitialize 関数"
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# SccInitialize 関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

この関数は、ソース管理プラグインを初期化し、機能および統合開発環境 \(IDE\) に制限を提供します。  
  
## 構文  
  
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
  
#### パラメーター  
 `ppvContext`  
 \[in\]ソース管理プラグインでは、ここでその context 構造体へのポインターを配置できます。  
  
 `hWnd`  
 \[in\]ソース管理プラグインは、それによって提供されるダイアログ ボックスの親として使用できる IDE ウィンドウへのハンドル。  
  
 `lpCallerName`  
 \[in\]ソース管理プラグインを呼び出し元のプログラムの名前。  
  
 `lpSccName`  
 \[入力、出力\]ソース管理プラグインが、独自の名前を格納するバッファー \(を超えないように `SCC_NAME_LEN`\)。  
  
 `lpSccCaps`  
 \[out\]ソース管理プラグインの機能フラグを返します。  
  
 `lpAuxPathLabel`  
 \[入力、出力\]ソース管理プラグインが説明する文字列を格納するバッファー、 `lpAuxProjPath` パラメーターによって返される、 [SccOpenProject](../extensibility/sccopenproject-function.md) と [SccGetProjPath](../extensibility/sccgetprojpath-function.md) \(を超えないように `SCC_AUXLABEL_LEN`\)。  
  
 `pnCheckoutCommentLen`  
 \[out\]チェック アウトのコメントの最大許容サイズを返します。  
  
 `pnCommentLen`  
 \[out\]その他のコメントの最大許容サイズを返します。  
  
## 戻り値  
 この関数のソース コントロールのプラグインの実装は、次の値のいずれかを返す期待される結果します。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|ソース コントロールの初期化が成功しました。|  
|SCC\_E\_INITIALIZEFAILED|システムを初期化できませんでした。|  
|SCC\_E\_NOTAUTHORIZED|指定の操作を実行できません。|  
|SCC\_E\_NONSPECFICERROR|不特定のエラーです。ソース管理システムは初期化されませんでした。|  
  
## 解説  
 IDE は、ソース管理プラグインが初めて読み込まれるときに、この関数を呼び出します。 IDE プラグインへの呼び出し元の名前などの特定の情報を渡すようになります。 IDE のコメントと、プラグインの機能の許容最大長などの特定の情報も取得バックアップします。  
  
 `ppvContext` を指す、 `NULL` ポインター。 ソース管理プラグインが構造体を使用して独自の割り当てし、その構造体へのポインターを格納 `ppvContext`します。 IDE はこのポインターを渡してのどの VSSCI API 関数にプラグイン グローバル ストレージに頼らなくても利用可能なコンテキスト情報を持つことと、プラグインの複数のインスタンスをサポートすることができます。 ときにこの構造体を解放は、 [SccUninitialize](../extensibility/sccuninitialize-function.md) が呼び出されます。  
  
 `lpCallerName` と `lpSccName` パラメーター名を交換するには、IDE とソース管理プラグインを有効にします。 これらの名前は、複数のインスタンスを区別するためにだけ使用可能性がありますが実際に表示されるか、メニューまたはダイアログ ボックスでします。  
  
 `lpAuxPathLabel` パラメーターは、ソリューション ファイルに格納されてへの呼び出しでプラグインをソース管理に渡されたに補助プロジェクト パスを識別するコメントとして使用する文字列、 [SccOpenProject](../extensibility/sccopenproject-function.md)です。[!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] 文字列を使用して"SourceSafe プロジェクト:"です。この特定の文字列を使用しないように他のソース管理プラグインを使用する必要があります。  
  
 `lpSccCaps` パラメーターは、ソース管理プラグインのプラグインの機能を示すビットフラグを格納する場所です。 \(機能ビットフラグの一覧については、次を参照してください。 [機能フラグ](../extensibility/capability-flags.md)\)。 たとえば、プラグインは、機能の設定、呼び出し元から提供されるコールバック関数に結果を記述するプラグインのプランに SCC\_CAP\_TEXTOUT ビットかどうか。 バージョン管理の結果のウィンドウを作成する IDE この通知はします。  
  
## 参照  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)   
 [機能フラグ](../extensibility/capability-flags.md)