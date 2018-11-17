---
title: 'DA0029: サポートされていない CLR バージョンです | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51195b14be7bffe682f4ac8588e38c6f5bd56e58
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762518"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: サポートされていない CLR バージョンです。
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



