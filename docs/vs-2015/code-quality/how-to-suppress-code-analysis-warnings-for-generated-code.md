---
title: '方法: 生成されたコードに対するコード分析の警告を抑制 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 81bb371a3e16236e22ab3a1fd4ac5ab431f61512
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536178"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>方法: 生成されたコードに対するコード分析の警告を抑制する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[方法: 生成されたコードのコード分析警告を抑制する](https://docs.microsoft.com/visualstudio/code-quality/how-to-suppress-code-analysis-warnings-for-generated-code)します。  
  
マネージ コード コンパイラは、多くの場合、コードの迅速な開発を促進するプロジェクトに追加されるコードを生成します。 さらに、開発者は、アプリケーションを迅速に開発を支援するのにサード パーティ製ツールを使用する多くの場合にします。 これらのツールでは、プロジェクトに追加されるコードも生成します。  
  
 コード分析が生成されたコードで検出する規則違反を確認する場合があります。 ただし場合に、表示し、違反を含むコードを維持することはできません参照しない可能性があります。  
  
 **結果生成されたコードを表示しない**プロジェクトのコード分析プロパティ ページでチェック ボックスでは、サード パーティのツールによって生成されたコードからのコード分析の警告を表示するかどうかを選択することができます。  
  
> [!NOTE]
>  このオプションは抑制コード分析エラーと警告が生成されたコードからエラーと警告は、フォームとテンプレートに含まれる場合。 フォームまたはテンプレートのソース コードは表示することも保持することもできます。  
  
### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>生成されたコードをプロジェクトで警告を抑制するには  
  
1.  ソリューション エクスプ ローラーでプロジェクトを右クリックし、をクリックし、**プロパティ**します。  
  
2.  クリックして**コード分析**します。  
  
3.  選択、**結果生成されたコードを表示しない**チェック ボックスをオンします。



