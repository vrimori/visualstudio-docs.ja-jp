---
title: プロバイダーのシンボル |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed25959cd6afa7232555757e358a99836d93924b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54981481"
---
# <a name="symbol-provider"></a>シンボル プロバイダー
式エバリュエーターの実装は、変数や式を評価するために、言語コンパイラによって生成されたシンボリック デバッグ情報にアクセスする必要があります。 そのためには、シンボル ハンドラーとも呼ばれるシンボル プロバイダー (SP) のインターフェイスを使用します。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] プログラム データベース (PDB) シンボル ファイルの形式を使用したネイティブ コードとマネージ コードには、SPs を提供します。 強力ながない限り、プログラムをカスタム形式で格納されているシンボルを使用するために必要ながによって提供される SPs を使用することをお勧めします[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。  
  
## <a name="implementation-notes"></a>実装に関するメモ  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]デバッグ エンジンの期待に SPs を共通言語ランタイム (CLR) のインターフェイスを使用して対話します。 その結果、SP は、Visual Studio のデバッグ エンジンを作成するには、CLR をサポートする必要があります。 一部である、debugref.doc で見つかるすべての CLR デバッグのインターフェイスの完全な一覧の[!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]します。  
  
 SP は、カスタム デバッグ エンジンでのみ使用される、デバッグ エンジンのニーズに応じて自由に、SP を実装できます。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)