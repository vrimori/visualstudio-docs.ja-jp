---
title: 64 ビット アプリケーションの前提条件の展開 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], 64-bit
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- 64-bit applications [Visual Studio]
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 0f98a611b382f3884ede2e1e239944b9e584ab77
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538207"
---
# <a name="deploying-prerequisites-for-64-bit-applications"></a>64 ビット アプリケーションの配置のための必要条件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[64 ビット アプリケーションの展開の前提条件](https://docs.microsoft.com/visualstudio/deployment/deploying-prerequisites-for-64-bit-applications)します。  
  
ClickOnce の配置では、 64 ビット プラットフォームのアプリケーションのインストールをサポートします。 ターゲット プラットフォームは**x86** 32 ビット プラットフォームでは、 **x64** AMD64 および EM64T 命令セットをサポートするコンピューターと**Itanium** 64 ビット Itanium プロセッサ用。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 64 ビット アプリケーションのインストール時の必須コンポーネントとして使用できる再頒布可能パッケージを次の表に示します。  
  
 64 ビット コンポーネントを含まない必須コンポーネントを選択した場合、選択したパッケージは 64 ビット プラットフォームで使用できないことを示す警告が表示される可能性があります。  
  
|再頒布可能パッケージ|x64 サポート|IA64 サポート|  
|---------------------|-----------------|------------------|  
|[!INCLUDE[vsto_runtime](../includes/vsto-runtime-md.md)]|○|Ｘ|  
|Visual C++ 2010 ランタイム ライブラリ (IA64)|Ｘ|○|  
|Visual C++ 2010 ランタイム ライブラリ (x64)|○|Ｘ|  
|Microsoft .NET Framework 4 (x86 および x64)|○||  
|Microsoft .NET Framework 4 Client Profile (x86 および x64)|はい||  
  
## <a name="see-also"></a>関連項目  
 [アプリケーション、サービス、およびコンポーネントの配置](../deployment/deploying-applications-services-and-components.md)   
 [方法: ClickOnce アプリケーションと共に必須コンポーネントをインストールする](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [64 ビット アプリケーション](http://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)



