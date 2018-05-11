---
title: DSL 定義のプロパティ
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: be119703868316f2335f06174c9f21c2dddd2edc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="properties-of-a-dsl-definition"></a>DSL 定義のプロパティ
DslDefinition プロパティ定義*ドメイン固有言語*バージョン番号などのプロパティを定義します。 DslDefinition プロパティに表示されます、**プロパティ**ウィンドウで、ダイアグラムの空いている領域をクリックすると、*ドメイン固有言語デザイナー*です。

 詳細については、次を参照してください。[ドメイン固有言語の定義方法](../modeling/how-to-define-a-domain-specific-language.md)です。 これらのプロパティを使用する方法の詳細については、次を参照してください。[をカスタマイズすると、ドメイン固有言語の拡張](../modeling/customizing-and-extending-a-domain-specific-language.md)です。

 DslDefinition では、次の表に、プロパティがあります。

|プロパティ|説明|既定値|
|--------------|-----------------|-------------|
|アクセス修飾子|ドメイン クラスのアクセス修飾子がパブリックまたは内部かを判断します。|public|
|カスタム属性|カスタムは、ドメイン クラスの属性を定義します。<br /><br /> **注**属性を追加する [参照] ボタンを使用します。|\<なし >|
|会社名|システム レジストリの現在の会社名の名前。|現在の会社名|
|名前|このドメイン クラスの名前。|現在の名前|
|名前空間|名前空間は、このドメイン クラスに関連付けます。|現在の名前空間|
|パッケージ Guid|Guid、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]この DSL に対して生成されるパッケージ。|\<なし >|
|パッケージ Namespace|名前空間を[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]この DSL に対して生成されるパッケージ。|\<なし >|
|製品名|登録される製品の名前、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]この DSL に対して生成されるパッケージ。|\<なし >|
|メモ|このドメイン クラスに関連するメモします。|\<なし >|
|説明|このドメイン クラスの説明です。|\<なし >|
|表示名|このドメイン クラスの生成されたデザイナーで表示される名前です。|\<なし >|
|ヘルプ キーワード|このドメイン クラスに関連付けられているヘルプ キーワード。|\<なし >|
|ビルド|このドメイン固有言語定義のインクリメンタル ビルド番号です。|0|
|メジャー バージョン|このドメイン固有言語定義の増分のメジャー ビルド番号。|1|
|マイナー バージョン|このドメイン固有言語定義の増分のマイナー ビルド番号です。|0|
|リビジョン|増分のリビジョンは、このドメイン固有言語定義の数をビルドします。|0|

## <a name="see-also"></a>関連項目

- [ドメイン固有言語ツールの用語集](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)