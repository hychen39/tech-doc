# Lab 01: Hello JSF

 Unit 01: Hello JSF  
hychen39@gm.cyut.edu.tw  
 2018/7/31

## 目標

* 撰寫你的第一支  JSF 程式.
* 瞭解 JSF 程式如何產生動態網頁內容.

## 事前準備

* 下載並安裝 [Glassfish 5.0](http://download.oracle.com/glassfish/5.0/release/glassfish-5.0.zip%20)
* 下載並安裝 Netbeans

## User Story

* 使用者進入頁面後, 頁面顯示數個餐點的名稱. 
* 這些餐點的名稱是在 Server 端設定的內容.

## 實作程序

Step. 建立一個 JSF Managed Bean `beans.Dishes`

```java
/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package beans;

import java.util.Arrays;
import java.util.List;
import javax.inject.Named;
import javax.enterprise.context.RequestScoped;

/**
 *
 * @author user
 */
@Named(value = "dishes")
@RequestScoped
public class Dishes {

    List<String> menu;
    /**
     * Creates a new instance of Dishes
     */
    public Dishes() {
        menu = Arrays.asList("私房紅燒牛", "法式蝦蟹鮑魚菇", "皇朝海龍宴");
    }

    public List<String> getMenu() {
        return menu;
    }

    public void setMenu(List<String> menu) {
        this.menu = menu;
    }







}
```

Step. 建立以下的 JSF 頁面 `/index.xhtml`

```text
<?xml version='1.0' encoding='UTF-8' ?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml"
      xmlns:h="http://xmlns.jcp.org/jsf/html"
      xmlns:ui="http://xmlns.jcp.org/jsf/facelets">
    <h:head>
        <title>Facelet Title</title>
        <style>
            .dish-item {
                font-weight: bold;
                border: 1px black solid;
                border-radius: 0.5rem;
                margin-top: 0.5rem;
            }
        </style>
    </h:head>
    <h:body>
        <h1> 今日菜單 </h1>
        <ul>
            <ui:repeat value="#{dishes.menu}" var="dish">
                <li > 
                    <h:outputText styleClass="dish-item" value="${dish}" /> 
                </li>
            </ui:repeat>
        </ul>
    </h:body>
</html>
```

## 問題與討論

1. 如何從頁面存取 Java Object 內的資料?
2. Web 頁面中如何使用 CSS 樣式? 
3. Web 頁面中那一個不是 HTML 標籤? 這個標籤被誰解讀呢?
4. 前端開發者的工作範圍?

## 實作所需要的觀念

* Java EE Multi-Tier Architecture
* Application Container
* Life Cycle of the JSF Request Processing
* 伺服器端的標籤 \(Server Side Tags\)

