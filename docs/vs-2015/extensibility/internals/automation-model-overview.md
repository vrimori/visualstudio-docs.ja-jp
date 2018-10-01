---
title: オートメーション モデルの概要 |Microsoft Docs
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
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fdce23e892fe2fa14dc7f24f95d5744be2c67c39
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538167"
---
# <a name="automation-model-overview"></a>オートメーション モデルの概要
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[オートメーション モデルの概要](https://docs.microsoft.com/visualstudio/extensibility/internals/automation-model-overview)します。  
  
オートメーション モデルは、Visual Studio アドインまたは拡張機能を作成する対象となるオブジェクトのセットで構成されます。 アドインを Visual Studio 環境を操作および一般的なタスクを自動化できるアプリケーションは、します。 Visual Studio 拡張機能では、Visual Studio のカスタム コンポーネントを作成したり、テキスト エディターなどの標準的なコンポーネントの機能を追加することができます。  
  
## <a name="objects-in-the-automation-model"></a>オートメーション モデル内のオブジェクト  
 オートメーション モデルは、関連する一般的な環境の主要な側面を制御するオブジェクトのグループで構成されます。 次に、オートメーション モデルを構成するオブジェクトの広範なセットを示す図を示します。  
  
 ![Visual Studio オートメーション オブジェクト チャート](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Visual Studio オートメーション オブジェクト  
  
 詳細については、次を参照してください。 [Visual Studio 環境の拡張](http://msdn.microsoft.com/library/4173a963-7ac7-4966-9bb7-e28a9d9f6792)します。  
  
 環境では、さまざまな機能領域のモデルを提供します。 たとえば、コードで検索するさまざまな要素のコード モデルがあります。 さまざまなドキュメントの要素のドキュメントのモデルがあります。 1 つの領域では、プロジェクトの領域では、VSPackage のプロバイダーにとって特に重要です。 新しいプロジェクトの種類と同様に、オートメーション モデルに貢献する多くの場合は[!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]と[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]オートメーション モデルに貢献します。 プロセスが記載されている[Vspackage の自動化を提供する](../../extensibility/internals/providing-automation-for-vspackages.md)します。  
  
 場所、環境のオートメーション モデルの拡張を検討することができます。  
  
-   プロジェクト  
  
-   ドキュメント  
  
-   コード  
  
-   ビルド  
  
 Automation の詳細については、次を参照してください。[オートメーションおよび for Visual Studio 機能拡張](http://msdn.microsoft.com/library/f71a2253-3e68-4e5e-9a18-edbba816caf6)します。 このドキュメントおよびドキュメントに、意思決定、VSPackage のオートメーションを提供する方法に関する役立つリンクを提供します。  
  
## <a name="see-also"></a>関連項目  
 [方法: アドインの作成](http://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)

