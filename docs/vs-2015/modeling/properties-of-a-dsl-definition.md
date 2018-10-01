---
title: DSL 定義のプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, definition file
ms.assetid: 38debcfe-e1a6-4a3f-9d69-3ab07520f2b6
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5c5ebb4672cdbb82692dc01339409ef7fa91c2d5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538227"
---
# <a name="properties-of-a-dsl-definition"></a>DSL 定義のプロパティ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[プロパティは DSL 定義の](https://docs.microsoft.com/visualstudio/modeling/properties-of-a-dsl-definition)します。  
  
DslDefinition プロパティ定義*ドメイン固有言語*バージョン番号などのプロパティを定義します。 DslDefinition プロパティに表示されます、**プロパティ**ウィンドウでは、図の空いている領域をクリックすると、*ドメイン固有言語デザイナー*します。  
  
 詳細については、次を参照してください。[ドメイン固有言語を定義する方法](../modeling/how-to-define-a-domain-specific-language.md)します。 これらのプロパティを使用する方法の詳細については、次を参照してください。[をカスタマイズすると、ドメイン固有言語を拡張する](../modeling/customizing-and-extending-a-domain-specific-language.md)します。  
  
 DslDefinition は次の表にプロパティを持ちます。  
  
|プロパティ|説明|既定値|  
|--------------|-----------------|-------------|  
|アクセス修飾子|ドメイン クラスのアクセス修飾子が public か internal かを判断します。|public|  
|カスタム属性|カスタムでは、ドメイン クラスに属性を定義します。<br /><br /> **注**属性を追加する参照ボタンを使用します。|\<なし >|  
|会社名|現在の会社名、システム レジストリの名前。|現在の会社名|  
|名前|このドメイン クラスの名前。|現在の名前|  
|名前空間|このドメイン クラスに関係する、名前空間。|現在の名前空間|  
|パッケージ Guid|Guid、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]パッケージがこの DSL 用に生成します。|\<なし >|  
|パッケージの Namespace|名前空間を[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]パッケージがこの DSL 用に生成します。|\<なし >|  
|製品名|登録される製品の名前、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]パッケージがこの DSL 用に生成します。|\<なし >|  
|メモ|このドメイン クラスに関連するメモします。|\<なし >|  
|説明|このドメイン クラスの説明です。|\<なし >|  
|表示名|このドメイン クラスの生成されたデザイナーに表示される名前です。|\<なし >|  
|ヘルプ キーワード|このドメイン クラスに関連付けられているヘルプ キーワード。|\<なし >|  
|ビルド|このドメイン固有言語定義のインクリメンタル ビルド番号。|0|  
|メジャー バージョン|このドメイン固有言語定義の増分のメジャー ビルド番号。|1|  
|マイナー バージョン|このドメイン固有言語定義の増分のマイナー ビルド番号。|0|  
|リビジョン|増分のリビジョンは、このドメイン固有言語定義の番号をビルドします。|0|  
  
## <a name="see-also"></a>関連項目  
 [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



