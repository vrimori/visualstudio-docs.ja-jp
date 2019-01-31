---
title: 識別子の入力候補 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense [JavaScript], statement completion
- statement completion, JavaScript IntelliSense
ms.assetid: c2cd4945-c67e-471b-8057-96cfd25f7fb2
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 89f507c2f4d01cf5e3e1e983cfcb5bafd9d9a7dd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54787653"
---
# <a name="statement-completion-for-identifiers"></a>識別子の入力候補
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

JavaScript をして入力変数の宣言を明示的に許可されていません。 その結果、IntelliSense がオブジェクトの入力候補一覧を常に提供することはできません。 これは、さまざまな状況で発生します。 いくつかの一般的なものを次に示します。  
  
- パラメーターが宣言されているが、これが呼び出されていない別の場所、アクティブなドキュメントでは、次の例に示すようにします。  
  
  ```javascript  
  function illuminate(light) {  
           light.  // Accurate statement completion is not available   
                   // unless illuminate is called elsewhere with a   
                   // parameter that has a value. If it is called only  
                   // in a function that is a sibling to   
                   // illuminate(light) in the call hierarchy, the   
                   // IntelliSense engine also cannot determine the   
                   // parameter type.  
       }  
  
  // Sibling function. No statement completion for light   
  // object in preceding code.  
  function lightLamp() {  
      var x = illuminate(1);  
  }  
  
  // Uncomment the next line to obtain statement completion for  
  // light object in preceding code.  
  // var x = illuminate(1);  
  ```  
  
- オブジェクトは、イベントに応答して呼び出される関数です。 デザイン時に IntelliSense エンジンは、このような状況で使用されるオブジェクトの種類を判断できません。  
  
   IntelliSense エンジンによって決定されること、イベントを呼び出す、通常を使用して場合`addEventListener`アクティブなドキュメント内のイベントをより正確な IntelliSense 情報を提供します。  
  
  IntelliSense は、オブジェクトを識別できないときに、IntelliSense エンジンには、名前付きエンティティの場合、または、アクティブなドキュメントに存在する識別子を入力候補一覧が表示されます。 入力候補一覧にこれらの識別子が含まれている場合は、それらの横にある情報アイコンが表示されます。 さらに、各識別子のツールヒントにはでは、式が不明であることを示します。 次の図はステートメント入力候補オプションのオブジェクトの種類の`light`オブジェクトとそのプロパティが定義されていないためを識別できません。 ただし、`intensity`プロパティで使用されているために、識別子の一覧で使用できる、`illuminate`関数。  
  
  **識別できないオブジェクトの入力候補オプション**  
  
  ![識別子の JavaScript IntelliSense](../ide/media/js-intellisense-identifiers.png "js_intellisense_identifiers")  
  
  オブジェクトの入力候補一覧は、XML ドキュメントのコメントまたは JavaScript IntelliSense の拡張機能を使用してオーバーライドできます。 これらの機能を使用して行うことができますの種類の情報とわかりやすい IntelliSense の情報ができない可能性がありますそれ以外の場合とします。 詳細については、次を参照してください。 [JavaScript IntelliSense の拡張](../ide/extending-javascript-intellisense.md)と[XML ドキュメント コメントの作成](../ide/create-xml-documentation-comments-for-javascript-intellisense.md)です。  
  
## <a name="see-also"></a>「  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)
