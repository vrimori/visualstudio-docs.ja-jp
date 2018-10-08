---
title: プロバイダーのシンボル |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f09fbe350afff983bb5fefe880104201441430c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537817"
---
# <a name="symbol-provider"></a>シンボル プロバイダー
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[シンボル プロバイダー](https://docs.microsoft.com/visualstudio/extensibility/debugger/symbol-provider)します。  
  
式エバリュエーターの実装は、変数や式を評価するために、言語コンパイラによって生成されたシンボリック デバッグ情報にアクセスする必要があります。 そのためには、シンボル ハンドラーとも呼ばれるシンボル プロバイダー (SP) のインターフェイスを使用します。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] プログラム データベース (PDB) シンボル ファイルの形式を使用したネイティブ コードとマネージ コードには、SPs を提供します。 強力ながない限り、プログラムをカスタム形式で格納されているシンボルを使用するために必要ながによって提供される SPs を使用することをお勧めします[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。  
  
## <a name="implementation-notes"></a>実装に関する注意事項  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]デバッグ エンジンの期待に SPs を共通言語ランタイム (CLR) のインターフェイスを使用して対話します。 その結果、SP は、Visual Studio のデバッグ エンジンを作成するには、CLR をサポートする必要があります。 一部である、debugref.doc で見つかるすべての CLR デバッグのインターフェイスの完全な一覧の[!INCLUDE[winsdklong](../../includes/winsdklong-md.md)]します。  
  
 SP は、カスタム デバッグ エンジンでのみ使用される、デバッグ エンジンのニーズに応じて自由に、SP を実装できます。  
  
## <a name="see-also"></a>関連項目  
 [デバッガーのコンポーネント](../../extensibility/debugger/debugger-components.md)

