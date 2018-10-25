---
title: 'DA0029: サポートされていない CLR バージョンです | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5067c9f93a489c09962a9402f4fe7672cbd61108
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818446"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: サポートされていない CLR バージョンです

|||  
|-|-|  
|規則 ID|DA0029|  
|カテゴリ|プロファイリング ツールの使用|  
|プロファイル方法|コマンド ラインからのプロファイリング|  
|メッセージ|収集時に、サポートされていない CLR バージョンが検出されました。 マネージド シンボルが正しく解決されない可能性があります。|  
|規則の種類|情報。|  

## <a name="cause"></a>原因  
 プロファイリング ツールでサポートされていない [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] を使用するアプリケーションをプロファイリングしようとしています。  

## <a name="rule-description"></a>規則の説明  
 アプリケーションで実行されているマネージド コードのシンボルをプロファイリング ツールが解決できないため、この警告が発生します。 プロファイリング ツールは、[!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] を実行しているアプリケーションのマネージド コード シンボルを解決できません。  

## <a name="how-to-fix-violations"></a>違反の修正方法  
 なし。