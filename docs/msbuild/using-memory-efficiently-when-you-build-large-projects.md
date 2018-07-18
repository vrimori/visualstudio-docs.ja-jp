---
title: 大規模なプロジェクトのビルドにおけるメモリの効率的な使用 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 386a15bb0eb1d4fb88a89fc3683b7e0bdc088d6e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31568059"
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>大規模なプロジェクトのビルドにおけるメモリの効率的な使用
大規模プロジェクトには、多くの場合、サブプロジェクトやその他の依存関係が含まれています。それらがビルド時に大量のシステム メモリを使うことがあります。 利用できるシステム メモリが少なくなると、システム パフォーマンスが落ちることもあります。 旧バージョンの [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] プロジェクトがメモリに残ったか、バージョン 3.5 でプロジェクトが削除されましたが、後の取得のためにキャッシュにビルド結果が維持されました。  
  
 バージョン 4.0 では、このメモリ管理が自動的に処理されます。`UnloadProjectsOnCompletion` や `UseResultsCache` のようなプロパティをプロジェクトで使用する必要がありません。  
  
## <a name="see-also"></a>参照  
 [MSBuild での複数のプロジェクトの並行ビルド](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)