---
title: "オートメーション モデルの概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 208357343a3e77e29b1dc0a98b6159c5ac3f957e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="automation-model-overview"></a>オートメーション モデルの概要
オートメーション モデルは、Visual Studio アドインまたは拡張機能を記述する対象となるオブジェクトのセットで構成されます。 アドインでは、Visual Studio 環境を操作および一般的なタスクを自動化できるアプリケーションです。 Visual Studio 拡張機能では、Visual Studio のカスタム コンポーネントを作成したり、テキスト エディターなどの標準的なコンポーネントの機能を追加することができます。  
  
## <a name="objects-in-the-automation-model"></a>オートメーション モデル内のオブジェクト  
 オートメーション モデルは、一般的な環境の主要なファセットを制御するオブジェクトの関連するグループで構成されます。 オートメーション モデルを作成するオブジェクトの幅広いセットを示す図を次に示します。  
  
 ![Visual Studio オートメーション オブジェクト チャート](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Visual Studio オートメーション オブジェクト  
  
 詳細については、次を参照してください。 [Visual Studio 環境の拡張](http://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792)です。  
  
 環境では、複数の機能領域のモデルを提供します。 たとえば、コードで検索するさまざまな要素のコード モデルがあります。 さまざまなドキュメントの要素のドキュメント モデルがあります。 1 つの領域では、プロジェクトの領域は VSPackage のプロバイダーに特定の対象とします。 新しいプロジェクトの種類とほぼ同じ方法で、オートメーション モデルに貢献する多くの場合は[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]と[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]オートメーション モデルに寄与します。 プロセスに記載されている[の Vspackage 用を提供するオートメーション](../../extensibility/internals/providing-automation-for-vspackages.md)です。  
  
 場所は、環境のオートメーション モデルの拡張を検討することができます。  
  
-   プロジェクト  
  
-   ドキュメント  
  
-   コード  
  
-   ビルド  
  
 Automation の詳細については、次を参照してください。[オートメーションと拡張性 for Visual Studio](http://msdn.microsoft.com/Library/f71a2253-3e68-4e5e-9a18-edbba816caf6)です。 このドキュメントおよびドキュメントへのリンクを VSPackage の自動化を提供する必要がある方法に関する意思決定を提供します。  
  
## <a name="see-also"></a>参照  
 [方法: アドインの作成](http://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)