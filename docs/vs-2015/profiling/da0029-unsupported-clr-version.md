---
title: 'DA0029: サポートされていない CLR バージョンです | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df5deda533c21033d26af4b8dc08d98a5dafc583
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533291"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: サポートされていない CLR バージョンです。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[DA0029: サポートされていない CLR バージョン](https://docs.microsoft.com/visualstudio/profiling/da0029-unsupported-clr-version)します。  
  
規則 Id |DA0029 |  
|カテゴリ |プロファイリング ツールの使用 |  
|プロファイル方法 |コマンドラインからのプロファイリング |  
|メッセージ |コレクション中に、サポートされていない CLR バージョンが検出されました。 マネージド シンボルが正しく解決されない場合があります |。  
|規則の種類 |情報 |。  
  
## <a name="cause"></a>原因  
 プロファイリング ツールでサポートされていない [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)] を使用するアプリケーションをプロファイリングしようとしています。  
  
## <a name="rule-description"></a>規則の説明  
 アプリケーションで実行されているマネージド コードのシンボルをプロファイリング ツールが解決できないため、この警告が発生します。 プロファイリング ツールは、[!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)] を実行しているアプリケーションのマネージド コード シンボルを解決できません。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 なし。



