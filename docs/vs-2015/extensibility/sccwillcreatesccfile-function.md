---
title: SccWillCreateSccFile 関数 |Microsoft Docs
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
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 60152353eb7ef41af3abab9fcf06d81f425442dc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262997"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile 関数
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

この関数は、ソース管理プラグインは、MSSCCPRJ の作成をサポートするかどうかを決定します。指定されたファイルごとのファイルを SCC です。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
SCCRTN SccWillCreateSccFile(  
   LPVOID  pContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPBOOL  pbSccFiles  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pContext  
 [in]ソース管理プラグインのコンテキストのポインター。  
  
 nFiles  
 [in]含まれるファイル名の数、`lpFileNames`配列の長さと、`pbSccFiles`配列。  
  
 lpFileNames  
 [in]チェックする完全修飾ファイル名の配列 (呼び出し元が配列を割り当てる必要があります)。  
  
 pbSccFiles  
 [入力、出力]結果を格納する配列。  
  
## <a name="return-value"></a>戻り値  
 この関数のソース管理プラグイン実装は、次の値のいずれかを返すが必要です。  
  
|[値]|説明|  
|-----------|-----------------|  
|SCC_OK|成功。|  
|SCC_E_INVALIDFILEPATH|配列内のパスのいずれかが無効です。|  
|SCC_E_NONSPECIFICERROR|不特定のエラーです。|  
  
## <a name="remarks"></a>Remarks  
 この関数は、ソース管理プラグインが、MSSCCPRJ でのサポートを提供するかどうかを判断ファイルの一覧で呼び出されます。SCC ファイル (用、MSSCCPRJ の詳細については指定されたファイルごとします。SCC ファイルを参照してください[MSSCCPRJ します。SCC ファイル](../extensibility/mssccprj-scc-file.md))。 ソース管理プラグインは、MSSCCPRJ を作成する機能があるかどうかを宣言できます。宣言することでファイルを SCC`SCC_CAP_SCCFILE`の初期化中にします。 プラグイン返します`TRUE`または`FALSE`の 1 ファイルあたり、 `pbSccFiles` MSSCCPRJ がある特定のファイルのうちの配列。SCC のサポート。 プラグイン成功コードが関数から返された場合、返される配列内の値が受け入れられます。 失敗した場合、配列は無視されます。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API 関数](../extensibility/source-control-plug-in-api-functions.md)   
 [MSSCCPRJ.SCC File](../extensibility/mssccprj-scc-file.md)

