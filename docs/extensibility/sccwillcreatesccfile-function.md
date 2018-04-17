---
title: SccWillCreateSccFile 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af6da09badf0ffea4846d35fe00b4ca146243d64
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile 関数
この関数は、ソース管理プラグインが、MSSCCPRJ の作成をサポートするかどうかを判断します。指定されたファイルの各ファイルを SCC です。  
  
## <a name="syntax"></a>構文  
  
```cpp  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pContext  
 [in]ソース管理プラグイン コンテキスト ポインターです。  
  
 nFiles  
 [in]含まれているファイル名の数、`lpFileNames`配列の長さだけでなく、`pbSccFiles`配列。  
  
 lpFileNames  
 [in]チェックする完全修飾ファイル名の配列 (配列は呼び出し元が割り当てた必要があります)。  
  
 pbSccFiles  
 [入力、出力].結果を格納する配列。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返す考えられます。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|成功。|  
|SCC_E_INVALIDFILEPATH|配列内のパスのいずれかが正しくありません。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>コメント  
 この関数はかどうか、ソース管理プラグインで使用できるように、MSSCCPRJ を決定するファイルの一覧で呼び出されます。(詳細について、MSSCCPRJ 指定されたファイルの各 SCC ファイル。SCC ファイルを参照してください[MSSCCPRJ です。SCC ファイル](../extensibility/mssccprj-scc-file.md))。 ソース管理プラグインは、MSSCCPRJ を作成する機能があるかどうかを宣言できます。宣言することでファイルを SCC`SCC_CAP_SCCFILE`の初期化中にします。 プラグインを返します`TRUE`または`FALSE`でファイルごと、 `pbSccFiles` MSSCCPRJ がある特定のファイルのうちの配列。SCC サポートします。 プラグイン関数からサクセス コードが返された場合は、戻り値の配列内の値が受け入れられます。 失敗した場合、配列は無視されます。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [MSSCCPRJ.SCC File](../extensibility/mssccprj-scc-file.md)