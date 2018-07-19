---
title: 64 ビット アプリケーションの前提条件の展開 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 91935bc819987823f5a2f3ad0781e975c72f7e0d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077933"
---
# <a name="deploy-prerequisites-for-64-bit-applications"></a>64 ビット アプリケーションの前提条件を展開します。
ClickOnce の配置では、 64 ビット プラットフォームのアプリケーションのインストールをサポートします。 ターゲット プラットフォームは**x86** 32 ビット プラットフォームでは、 **x64** AMD64 および EM64T 命令セットをサポートするコンピューターと**Itanium** 64 ビット Itanium プロセッサ用。  
  
## <a name="prerequisites"></a>前提条件  
 64 ビット アプリケーションのインストール時の必須コンポーネントとして使用できる再頒布可能パッケージを次の表に示します。  
  
 64 ビット コンポーネントを含まない必須コンポーネントを選択した場合、選択したパッケージは 64 ビット プラットフォームで使用できないことを示す警告が表示される可能性があります。  
  
|再頒布可能パッケージ|x64 サポート|IA64 サポート|  
|---------------------|-----------------|------------------|  
|[!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)]|○|Ｘ|  
|Visual C++ 2010 ランタイム ライブラリ (IA64)|Ｘ|[はい]|  
|Visual C++ 2010 ランタイム ライブラリ (x64)|[はい]|Ｘ|  
|Microsoft .NET Framework 4 (x86 および x64)|○||  
|Microsoft .NET Framework 4 Client Profile (x86 および x64)|[はい]||  
  
## <a name="see-also"></a>関連項目  
 [アプリケーション、サービス、およびコンポーネントをデプロイします。](../deployment/deploying-applications-services-and-components.md)   
 [方法: ClickOnce アプリケーションと共に必須コンポーネントをインストールします。](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [64 ビット アプリケーション](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)