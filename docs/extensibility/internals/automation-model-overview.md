---
title: "オートメーション モデルの概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: ce59c002accd55b9179cacc60cf944ff72138c7e
ms.lasthandoff: 02/22/2017

---
# <a name="automation-model-overview"></a>オートメーション モデルの概要
オートメーション モデルは、Visual Studio アドインまたは拡張機能を作成する対象となるオブジェクトのセットで構成されます。 アドインによって、Visual Studio 環境を操作でき、一般的なタスクを自動化するアプリケーションです。 Visual Studio 拡張機能では、Visual Studio のカスタム コンポーネントを作成したり、テキスト エディターなどの標準的なコンポーネントの機能を追加することができます。  
  
## <a name="objects-in-the-automation-model"></a>オートメーション モデル内のオブジェクト  
 オートメーション モデルは、関連の一般的な環境の主要な側面を制御するオブジェクトのグループで構成されます。 オートメーション モデルを構成するオブジェクトの広範なセットを示す図を次に示します。  
  
 ![Visual Studio オートメーション オブジェクト チャート](~/extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Visual Studio オートメーション オブジェクト  
  
 詳細については、次を参照してください。 [Visual Studio 環境の拡張](http://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792)します。  
  
 環境では、さまざまな機能領域のモデルを提供します。 たとえば、コードで検索するさまざまな要素のコード モデルが存在します。 さまざまなドキュメントの要素のドキュメント モデルがあります。 1 つの領域では、プロジェクトの領域では、VSPackage プロバイダーにとって特に重要です。 新しいプロジェクトの種類と同様に、オートメーション モデルに貢献する多くの場合は[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]と[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]オートメーション モデルに寄与します。 プロセスは「 [VSPackages に提供するオートメーション](../../extensibility/internals/providing-automation-for-vspackages.md)します。  
  
 場所は、環境のオートメーション モデルの拡張を検討することができます。  
  
-   プロジェクト  
  
-   ドキュメント  
  
-   コード  
  
-   ビルド  
  
 オートメーションの詳細については、次を参照してください。[オートメーションと Visual Studio の機能拡張](http://msdn.microsoft.com/Library/f71a2253-3e68-4e5e-9a18-edbba816caf6)します。 このドキュメントおよびドキュメントへのリンクを VSPackage のための自動化を提供する方法に関する意思決定を支援を提供します。  
  
## <a name="see-also"></a>関連項目  
 [方法: アドインの作成](http://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
