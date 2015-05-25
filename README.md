

~~~

--# Clicker
Clicker = class()

function Clicker:init(pos, cost, incm, speed)
    -- you can accept and set parameters here
    self.pos = pos
    self.cost = cost
    self.incm = incm
    self.speed = speed
    
    self.earn = false
    self.earnw = 0
    self.amount = 0
end

function Clicker:draw()
    -- Codea does not automatically call this method
    fill(255, 0, 0, 255)
    rect(self.pos.x-100, self.pos.y-15, 50, 30)
    fill(44, 255, 0, 255)
    fontSize(30)
    font("ArialMT")
    text("Buy", self.pos.x, self.pos.y)
    fontSize(15)
    fill(0, 0, 0, 255)
    text(self.amount, self.pos.x-110, self.pos.y)
    text("Cost:"..self.cost, self.pos.x-100, self.pos.y-30)
    text("Income:"..self.incm*self.amount, self.pos.x, self.pos.y-30)
    
    --Earning process
    if self.earn == true then
        fill(255, 249, 0, 255)
        rect(self.pos.x+50, self.pos.y-15, self.earnw, 30)
    if self.earnw<=99 then
            self.earnw=self.earnw+self.speed
    elseif self.earnw>=100 then
            cash = cash+self.incm*self.amount
            self.earnw=0
            sound("Game Sounds One:Wall Bounce 2")
            self.earn = false
        end
    end
end

function Clicker:touched(t)
    -- Codea does not automatically call this method
    if self.earnw==0 then
        if t.x>self.pos.x-100 and t.x<self.pos.x-50 and t.y>self.pos.y-15 and t.y<self.pos.y+15 and 
        t.state == ENDED then
        self. earn = true
        sound("Game Sounds One:Wall Bounce 1")
            end
        end
    if self.cost<=cash then
    if t.x>self.pos.x-30 and t.x<self.pos.x+40 and t.y>self.pos.y-20 and t.y<self.pos.y+20 and t.state==ENDED then
            sound("Game Sounds One:Assembly 4")
            self.amount = self.amount+1
            cash = cash - self.cost
            self.cost = self.cost + math.ceil(self.cost/4)
        end
    elseif self.cost>cash and t.x>self.pos.x-30 and t.x<self.pos.x+40 and
        t.y>self.pos.y-20 and t.y<self.pos.y+20 and t.state==ENDED then
        sound("Game Sounds One:Wrong")
    end
end

--# Main
-- Time Management Game
displayMode(FULLSCREEN)
-- Use this function to perform your initial setup
function setup()
    music("Game Music One:Funk Blue Cube", true, 0.5)
    cash = 10
    
    --Clickers
    C1 = Clicker(vec2(200, HEIGHT-200), 5, 10, 3)
    C2 = Clicker(vec2(200, HEIGHT-350), 100, 100, 2.5)
    C3 = Clicker(vec2(200, HEIGHT-500), 500, 300, 2)
    C4 = Clicker(vec2(200, HEIGHT-650), 10000, 900, 1.5)
    
    C5 = Clicker(vec2(WIDTH-200, HEIGHT-200), 50000, 2700, 1)
    C6 = Clicker(vec2(WIDTH-200, HEIGHT-350), 100000, 8100, 1)
    C7 = Clicker(vec2(WIDTH-200, HEIGHT-500), 500000, 24300, 1)
    C8 = Clicker(vec2(WIDTH-200, HEIGHT-650), 1000000, 72900, 1)
    
end

-- This function gets called once every frame
function draw()
    -- This sets a dark background color
    background(240, 240, 240, 255)
    
    
     --Clickers
    C1:draw()
    if C1.amount>=10 then
    C2:draw()
    if C2.amount>=10 then
    C3:draw()
    if C3.amount>=10 then
    C4:draw()
    
    if C4.amount>=10 then
    C5:draw()
    if C5.amount>=10 then
    C6:draw()
    if C6.amount>=10 then
    C7:draw()
    if C7.amount>=10 then
    C8:draw()
                                end
                            end
                        end
                    end
                end
            end
        end
    
    --Money
    fontSize(30)
    font("Arial-BoldMT")
    fill(46, 251, 9, 255)
    text("Cash:".."$"..cash, 150, HEIGHT-70)
end

function touched(t)
    --Clickers
    C1:touched(t)
    if C1.amount>=10 then
    C2:touched(t)
    if C1.amount>=10 then
    C3:touched(t)
    if C1.amount>=10 then
    C4:touched(t)
    
    if C1.amount>=10 then
    C5:touched(t)
    if C1.amount>=10 then
    C6:touched(t)
    if C1.amount>=10 then
    C7:touched(t)
    if C1.amount>=10 then
    C8:touched(t)
                                end
                            end
                        end
                    end
                end
            end
        end
end

~~~
