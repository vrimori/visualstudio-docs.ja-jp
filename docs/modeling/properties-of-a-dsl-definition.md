---
title: "DSL 定義のプロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, definition file
ms.assetid: 38debcfe-e1a6-4a3f-9d69-3ab07520f2b6
caps.latest.revision: 13
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 7a8fc0474f624785a47a4ba9f970b5a1ca54dd9c
ms.lasthandoff: 02/22/2017

---
# <a name="properties-of-a-dsl-definition"></a>DSL 定義のプロパティ
DslDefinition プロパティを定義する*ドメイン固有言語*バージョン番号などのプロパティを定義します。 DslDefinition プロパティに表示されます、**プロパティ**ウィンドウでは、図の空いている領域をクリックすると、*ドメイン固有言語デザイナー*します。  
  
 詳細については、次を参照してください。[ドメイン固有言語を定義する方法](../modeling/how-to-define-a-domain-specific-language.md)します。 これらのプロパティを使用する方法の詳細については、次を参照してください。[をカスタマイズすると、ドメイン固有言語を拡張する](../modeling/customizing-and-extending-a-domain-specific-language.md)です。  
  
 DslDefinition では、次の表に、プロパティがあります。  
  
|プロパティ|説明|既定値|  
|--------------|-----------------|-------------|  
|アクセス修飾子|ドメイン クラスのアクセス修飾子がパブリックまたは内部かを判断します。|public|  
|カスタム属性|カスタムは、ドメイン クラスの属性を定義します。<br /><br /> **注**属性を追加する [参照] ボタンを使用します。|\<[なし] >|  
|会社名|システム レジストリの現在の会社名の名前です。|現在の会社名|  
|名前|このドメイン クラスの名前。|現在の名前|  
|Namespace|名前空間は、このドメイン クラスと連携します。|現在の名前空間|  
|パッケージ Guid|Guid、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]パッケージがこの DSL を生成します。|\<[なし] >|  
|パッケージの Namespace|名前空間を[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]パッケージがこの DSL を生成します。|\<[なし] >|  
|製品名|用に登録される製品の名前、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]パッケージがこの DSL を生成します。|\<[なし] >|  
|ノート|このドメイン クラスに関連するメモします。|\<[なし] >|  
|説明|このドメイン クラスの説明です。|\<[なし] >|  
|表示名|このドメイン クラスを生成されたデザイナーで表示される名前です。|\<[なし] >|  
|ヘルプ キーワード|このドメイン クラスに関連付けられているヘルプ キーワードです。|\<[なし] >|  
|ビルド|このドメイン固有言語定義の増分ビルド番号。|0|  
|メジャー バージョン|このドメイン固有言語定義の増分のメジャー ビルド番号。|1|  
|マイナー バージョン|このドメイン固有言語定義の増分のマイナー ビルド番号。|0|  
|Revision|増分のリビジョンは、このドメイン固有言語定義用の番号をビルドします。|0|  
  
## <a name="see-also"></a>関連項目  
 [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)
