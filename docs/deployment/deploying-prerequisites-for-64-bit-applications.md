---
title: "64 ビット アプリケーションの前提条件を展開する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
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
caps.latest.revision: "23"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 6e0134b0a0a6151b6ae6544f1ad8272a6d4cac47
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-prerequisites-for-64-bit-applications"></a>64 ビット アプリケーションの配置のための必要条件
ClickOnce の配置では、 64 ビット プラットフォームのアプリケーションのインストールをサポートします。 ターゲット プラットフォームは**x86** 32 ビット プラットフォームでは、 **x64** AMD64 と EM64T 命令セットをサポートするコンピューターと**Itanium** 64 ビット Itanium プロセッサ用です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 64 ビット アプリケーションのインストール時の必須コンポーネントとして使用できる再頒布可能パッケージを次の表に示します。  
  
 64 ビット コンポーネントを含まない必須コンポーネントを選択した場合、選択したパッケージは 64 ビット プラットフォームで使用できないことを示す警告が表示される可能性があります。  
  
|再頒布可能パッケージ|x64 サポート|IA64 サポート|  
|---------------------|-----------------|------------------|  
|[!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)]|○|Ｘ|  
|Visual C++ 2010 ランタイム ライブラリ (IA64)|Ｘ|○|  
|Visual C++ 2010 ランタイム ライブラリ (x64)|○|Ｘ|  
|Microsoft .NET Framework 4 (x86 および x64)|○||  
|Microsoft .NET Framework 4 Client Profile (x86 および x64)|[はい]||  
  
## <a name="see-also"></a>参照  
 [アプリケーション、サービス、およびコンポーネントを展開します。](../deployment/deploying-applications-services-and-components.md)   
 [方法: ClickOnce アプリケーションと共に必須コンポーネントをインストールする](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [64 ビット アプリケーション](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)