---
title: 大規模なプロジェクトのビルドにおけるメモリの効率的な使用 | Microsoft Docs
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
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2cb204fcfb5a96fe9833571895513dfda4449b8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539508"
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>大規模なプロジェクトのビルドにおけるメモリの効率的な使用
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[を使用してメモリ効率的とする大規模なプロジェクトを構築](https://docs.microsoft.com/visualstudio/msbuild/using-memory-efficiently-when-you-build-large-projects)します。  
  
  
大規模プロジェクトには、多くの場合、サブプロジェクトやその他の依存関係が含まれています。それらがビルド時に大量のシステム メモリを使うことがあります。 利用できるシステム メモリが少なくなると、システム パフォーマンスが落ちることもあります。 旧バージョンの [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] プロジェクトがメモリに残ったか、バージョン 3.5 でプロジェクトが削除されましたが、後の取得のためにキャッシュにビルド結果が維持されました。  
  
 バージョン 4.0 では、このメモリ管理が自動的に処理されます。`UnloadProjectsOnCompletion` や `UseResultsCache` のようなプロパティをプロジェクトで使用する必要がありません。  
  
## <a name="see-also"></a>関連項目  
 [MSBuild での複数のプロジェクトの並行ビルド](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)



