---
title: オートメーション モデルの概要 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cb9176ce0341ff50bb59a9666d18ae5054dad872
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53821848"
---
# <a name="automation-model-overview"></a>オートメーション モデルの概要
オートメーション モデルは、Visual Studio アドインまたは拡張機能を作成する対象となるオブジェクトのセットで構成されます。 アドインを Visual Studio 環境を操作および一般的なタスクを自動化できるアプリケーションは、します。 Visual Studio 拡張機能では、Visual Studio のカスタム コンポーネントを作成したり、テキスト エディターなどの標準的なコンポーネントの機能を追加することができます。  
  
## <a name="objects-in-the-automation-model"></a>オートメーション モデル内のオブジェクト  
 オートメーション モデルは、関連する一般的な環境の主要な側面を制御するオブジェクトのグループで構成されます。 次の図は、オートメーション モデルを作成するオブジェクトを Visual Studio の広範なセットを示します。  
  
 ![Visual Studio オートメーション オブジェクト チャート](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
  
 詳細については、次を参照してください。 [Visual Studio 環境の拡張](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792)します。  
  
 環境では、さまざまな機能領域のモデルを提供します。 たとえば、コードで検索するさまざまな要素のコード モデルがあります。 さまざまなドキュメントの要素のドキュメントのモデルがあります。 1 つの領域では、プロジェクトの領域では、VSPackage のプロバイダーにとって特に重要です。 新しいプロジェクトの種類と同様に、オートメーション モデルに貢献する多くの場合は[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]と[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]オートメーション モデルに貢献します。 プロセスが記載されている[Vspackage 自動化](../../extensibility/internals/providing-automation-for-vspackages.md)します。  
  
 場所、環境のオートメーション モデルの拡張を検討することができます。  
  
-   プロジェクト  
  
-   ドキュメント  
  
-   コード  
  
-   ビルド  

  
Automation の詳細については、次を参照してください。[オートメーションおよび for Visual Studio 機能拡張](../extensibility-in-visual-studio.md)します。 このドキュメントおよびドキュメントに、意思決定、VSPackage のオートメーションを提供する方法に関する役立つリンクを提供します。  
  
## <a name="see-also"></a>関連項目  
 [方法: アドインを作成します。](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)