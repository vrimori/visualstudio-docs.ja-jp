---
title: "プロバイダーのシンボル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e0f01e10050fcbdb5cf27390464ae6b8b3e62d64
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="symbol-provider"></a>プロバイダーのシンボル
式エバリュエーターの実装は、変数や式を評価するために、言語コンパイラによって生成されたシンボリック デバッグ情報にアクセスする必要があります。 これには、シンボル ハンドラーとも呼ばれます。 シンボル プロバイダー (SP) のインターフェイスを使用します。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]プログラム データベース (PDB) のシンボル ファイル形式を使用してネイティブ コードとマネージ コードには、Sp を提供します。 カスタム形式で格納されているシンボルを使用するプログラムの必要がない限り、強力なは、によって提供される Sp を使用することをお勧め[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。  
  
## <a name="implementation-notes"></a>実装に関するメモ  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Sp が共通言語ランタイム (CLR) インターフェイスを使用するとの対話形式デバッグ エンジンが予想されます。 その結果、Visual Studio のデバッグ エンジンを操作する SP が CLR をサポートする必要があります。 すべての CLR デバッグ インターフェイスの完全な一覧は含まれて含まれている debugref.doc の[!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]です。  
  
 稼働する場合は、SP は、カスタム デバッグ エンジンでのみ、必要に応じて、デバッグ エンジンのニーズに応じて、SP を実装できます。  
  
## <a name="see-also"></a>参照  
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)