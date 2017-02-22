---
title: "Windows API 関数をデバッグするには | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.api"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "API, デバッグ"
  - "デバッグ [C++], Windows API 関数"
  - "NT シンボルと Windows API 関数のデバッグ"
  - "Windows API 関数, デバッグ"
  - "Windows API, デバッグ (API 関数を)"
ms.assetid: 7c126f57-62ab-4d94-9805-632d696ba1f0
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Windows API 関数をデバッグするには
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

NT シンボルを読み込んだ状態で Windows API 関数をデバッグするには、次の手順を実行する必要があります。  
  
### NT シンボルを読み込んだ状態で Windows API 関数にブレークポイントを設定するには  
  
-   関数の名前と、関数が存在する DLL の名前を入力します。  32 ビット コードでは、関数名の装飾形式を使用します。  たとえば、**MessageBeep** にブレークポイントを設定するには、次のように入力します。  
  
    ```  
    {,,USER32.DLL}_MessageBeep@4  
    ```  
  
     装飾名を取得する方法については、「[Viewing Decorated Names](http://msdn.microsoft.com/ja-jp/f79e2717-a4db-4d12-a689-69830cce2be0)」を参照してください。  
  
## 参照  
 [ネイティブ コードのデバッグに関する FAQ](../debugger/debugging-native-code-faqs.md)   
 [ネイティブ コードのデバッグ](../debugger/debugging-native-code.md)